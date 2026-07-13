# Painel Administrativo Zeyro — Especificação Técnica

> **Operador:** Nailto
> **Stack:** Flutter Web 3.41 + Firebase (Auth, Firestore, Storage, Crashlytics)
> **Deploy:** VPS Linux (Nginx reverse proxy + certificado SSL)
> **Data:** 2026-07-13

---

## Sumário

1. [Escopo do Produto](#1-escopo-do-produto)
2. [Estrutura de Telas](#2-estrutura-de-telas)
3. [Entidades e Coleções Firestore](#3-entidades-e-coleções-firestore)
4. [Regras de Negócio Aplicáveis](#4-regras-de-negócio-aplicáveis)
5. [Autenticação e Segurança](#5-autenticação-e-segurança)
6. [Stack Técnica e Dependências](#6-stack-técnica-e-dependências)
7. [Requisitos Mínimos de VPS](#7-requisitos-mínimos-de-vps)
8. [Build e Deploy](#8-build-e-deploy)
9. [Prioridade de Implementação](#9-prioridade-de-implementação)

---

## 1. Escopo do Produto

### 1.1 O que é

Painel web operacional para administração da plataforma Zeyro. O Nailto (admin) precisa:
- **Ver** o que está acontecendo (dashboard, relatórios)
- **Gerir** os atores da plataforma (candidatos, instrutores)
- **Intervir** em conflitos (denúncias, disputas, estornos)
- **Operar** o financeiro (saques, créditos, reembolsos)
- **Configurar** parâmetros do sistema (valor aula, mínimos, textos)

### 1.2 O que NÃO é

- Não é app mobile — é web exclusivo (desktop-first)
- Não é auto-serve — só o admin opera
- Não tem cadastro aberto — contas criadas manualmente via Firebase Console
- Não substitui o backend (Node.js) — apenas consome dados do Firestore

### 1.3 Perfil de uso

| Característica | Valor |
|---------------|-------|
| Usuários simultâneos | 1–3 (admin + suporte) |
| Requisições/dia | ~100–500 (consultas e ações pontuais) |
| Dados trafegados | Leve — maioria texto + números |
| Criticalidade | Média — downtime não afeta app principal |

---

## 2. Estrutura de Telas

### 2.1 AdminShell (Layout Base)

```
┌──────────────────────────────────────────────┐
│  🟢 Zeyro Admin    [Notificações] [Avatar]   │ ← Topbar
├──────────┬───────────────────────────────────┤
│ Sidebar  │  Conteúdo Principal               │
│          │                                   │
│ 📊 Dash  │  (renderizado conforme rota)      │
│ 👥 Usu.  │                                   │
│ 📚 Aulas │                                   │
│ 💰 Pag.  │                                   │
│ 🚨 Den.  │                                   │
│ 💳 Fin.  │                                   │
│ 📈 Rel.  │                                   │
│ ⚙️ Conf. │                                   │
└──────────┴───────────────────────────────────┘
```

Sidebar responsiva: em desktop ≤1200px, recolhível a ícones. Em mobile não aplica (painel é desktop-first).

### 2.2 Dashboard (`/admin`)

Cards de resumo com refresh automático a cada 60s:

| Card | Coleção | Query |
|------|---------|-------|
| 👥 Candidatos | `candidatos` | total count |
| 👤 Instrutores | `instrutores` | count where status != bloqueado |
| ✅ Aulas hoje | `aulas` | where `data_hora == hoje` |
| ⏳ Aulas pendentes | `aulas` | where `status == agendada` |
| 💰 Receita mês | `pagamentos` | where `status == aprovado && createdAt >= mes_atual`, sum valor |
| 🚨 Denúncias abertas | `denuncias` | where `status == aberta`, count |
| 💳 Saques pendentes | `regras_financeiras` | where `tipo == saque && status == solicitado_saque`, count |
| ⭐ Avaliações hoje | `avaliacoes` | where `createdAt >= hoje` |

Adicional: gráfico de linha (aulas/dia nos últimos 30 dias) usando `fl_chart`.

### 2.3 Usuários (`/admin/usuarios`)

**Lista** com `DataTable` paginada:

| Coluna | Fonte |
|--------|-------|
| Nome | `users.nome` |
| Email | `users.email` |
| Role | `users.role` (candidato/instrutor/admin) |
| Status | `instrutores.status` ou `candidatos.instrutorId != null` |
| Cadastro | `users.createdAt` |
| Ações | dropdown (ver, bloquear, alterar role) |

**Filtros:** nome (texto), email, role (select), status (select)

**Detalhe do usuário** (`/admin/usuarios/:id`):
- Dados cadastrais completos (do `User` + `Candidato` ou `Instrutor`)
- Se instrutor: nota média, alunos atendidos, status do veículo, documentos
- Se candidato: situação CNH, categoria, aulas compradas/restantes
- Histórico de aulas (tabela com status)
- Histórico de pagamentos
- Denúncias recebidas (se houver)
- Ação: **Bloquear/Desbloquear** (muda `users` ou `instrutores.status = 'bloqueado'`)

### 2.4 Aulas (`/admin/aulas`)

**Lista** com filtros:

| Filtro | Tipo |
|--------|------|
| Status | Select: agendada / concluida / cancelada / em_disputa |
| Instrutor | Select (carregado de `instrutores`) |
| Candidato | Texto (busca por nome) |
| Data | Date range picker |

**Ações na linha:**
- 👁️ Ver detalhes
- ❌ Cancelar (com motivo + regra financeira aplicada)
- ⚖️ Marcar como disputa (abre para análise)
- 💰 Reembolsar (aciona estorno via regra financeira)

**Detalhe** (`/admin/aulas/:id`):
- Dados completos da `Aula` (candidato, instrutor, datas, valor, tipo veículo)
- Status history (timeline vertical)
- Pagamento vinculado
- Chat entre candidato e instrutor (somente leitura)
- Avaliação do candidato (se existir)
- Ações: Cancelar / Reembolsar / Marcar como resolvida

### 2.5 Pagamentos (`/admin/pagamentos`)

**Lista** com filtros:

| Filtro | Tipo |
|--------|------|
| Status | Select: aprovado / pendente / estornado / cancelado |
| Método | Select: pix / credit_card / boleto / mercado_pago |
| Período | Date range picker |
| Valor | Range slider (min-max) |

**Colunas:** ID, Candidato, Instrutor, Valor, Método, Status, Data, Ações

**Ações:** Visualizar detalhes, Reembolsar (com confirmação)

**Detalhe** (`/admin/pagamentos/:id`):
- Dados do `Pagamento` (todos os campos MP)
- QR Code Pix (exibir imagem se `pix_qr_code_base64`)
- Link checkout MP (`mp_checkout_url`)
- Aula vinculada
- Regra financeira gerada (se houver)

### 2.6 Denúncias (`/admin/denuncias`)

**Menu principal para o Nailto.** Tolerância zero significa que denúncias precisam de resposta rápida.

**Lista** com filtros:

| Filtro | Tipo |
|--------|------|
| Status | Select: aberta / em_analise / resolvida / fechada |
| Data | Date range |
| Denunciado | Texto (nome ou ID) |

**Colunas:** ID, Denunciante, Denunciado, Motivo, Data, Status, Ações

**Badge vermelho** no sidebar quando há denúncias `abertas`.

**Detalhe** (`/admin/denuncias/:id`):
- Motivo e descrição completa
- Mídia anexada (se `midia_url` existir, exibir player/imagem)
- Aula vinculada
- Histórico de denúncias do denunciado (quantas, resolvidas, status atual)
- **Ações:**
  - ✅ **Arquivar** (status → `fechada`, sem penalidade)
  - ⚠️ **Advertir** (status → `resolvida`, envia notificação)
  - 🔴 **Bloquear conta** (status → `resolvida`, `instrutores.status = 'bloqueado'` ou atualiza `users`)

**Auto-block implementado:** sistema já bloqueia automaticamente após 3 denúncias. Admin pode reverter.

### 2.7 Financeiro (`/admin/financeiro`)

**Sub-menus:**

#### 2.7.1 Saques (`/admin/financeiro/saques`)

| Coluna | Fonte |
|--------|-------|
| Instrutor | `regras_financeiras.userId` → join `users.nome` |
| Valor | `regras_financeiras.valor` |
| Data | `regras_financeiras.createdAt` |
| Status | `regras_financeiras.status` (solicitado_saque / disponivel / utilizado) |
| Ações | ✅ Aprovar (marca como pago manualmente) |

**Regra:** Saque mínimo R$500 implementada no `RegrasFinanceirasService.podeSacar()`.

#### 2.7.2 Extrato do Instrutor (`/admin/financeiro/instrutor/:id`)

- Saldo disponível (soma de `credito_cancelamento` + `credito_falta` com `status == disponivel`)
- Histórico de créditos e débitos
- Saques realizados

#### 2.7.3 Estornos (`/admin/financeiro/estornos`)

- Lista de pagamentos estornados
- Motivo do estorno
- Valor e data

### 2.8 Relatórios (`/admin/relatorios`)

**Exportáveis em CSV** (botão download gera arquivo no cliente):

| Relatório | Query |
|-----------|-------|
| Faturamento mensal | `pagamentos` group by month, sum valor |
| Instrutores top | `instrutores` ordenado por `alunosAtendidos` + `notaMedia` |
| Cancelamentos/Faltas | `aulas` where `status == cancelada`, group by `instrutor_id` ou `candidato_id` |
| Denúncias | `denuncias` group by status, motivo, mês |
| Aulas por período | `aulas` group by data, com total de valor |

**Filtro de período comum:** 7 dias, 30 dias, 90 dias, personalizado.

### 2.9 Configurações (`/admin/configuracoes`)

| Parâmetro | Tipo | Onde impacta |
|-----------|------|-------------|
| Valor da aula (R$) | `double` | `AppConfig.valorAula` + salvo no Firestore (doc `config/sistema`) |
| Aulas mínimas | `int` | `AppConfig.aulasMinimas` |
| Saque mínimo (R$) | `double` | `RegrasFinanceirasService.podeSacar()` |
| Percentual plataforma cancelamento -24h | `double` | Regra: R$25 atualmente (25%) |
| Percentual instrutor falta | `double` | Regra: R$25 atualmente (25%) |
| Texto FAQ | `string` (rich text) | Tela de suporte do app |
| Contato suporte | `string` | Email/whatsapp exibido no app |

**Persistência:** documento `config/sistema` no Firestore com `Map<String, dynamic>`.

---

## 3. Entidades e Coleções Firestore

Mapeamento completo das 10 coleções que o admin precisa acessar:

| Coleção | Modelo | Admin precisa: |
|---------|--------|----------------|
| `users/{id}` | User | CRUD (bloquear, alterar role) |
| `candidatos/{id}` | Candidato | R (visualizar + dados do perfil/pacote) |
| `instrutores/{id}` | Instrutor | CRUD (bloquear, aprovar) |
| `aulas/{id}` | Aula | CRUD (cancelar, forçar status) |
| `pagamentos/{id}` | Pagamento | R + estorno |
| `avaliacoes/{id}` | Avaliacao | R (consulta) |
| `denuncias/{id}` | Denuncia | CRUD (analisar, resolver) |
| `regras_financeiras/{id}` | RegraFinanceira | R + aprovar saque |
| `mensagens/{id}` | Mensagem | R (somente leitura via detalhe da aula) |
| `notificacoes/{id}` | — | R (auditoria) |

**Coleções auxiliares que o admin NÃO mexe:**
- `config/sistema` — parâmetros (escrita pelo admin via tela Configurações)

---

## 4. Regras de Negócio Aplicáveis

São as mesmas do app, mas o admin pode **sobrescrever** ou **forçar**:

| Regra | App | Admin |
|-------|-----|-------|
| Cancelamento +24h | 100% crédito | Pode estornar valor integral |
| Cancelamento -24h | R$50 crédito / R$25 instrutor / R$25 plataforma | Pode reverter |
| Falta | R$25 instrutor / R$75 plataforma | Pode perdoar |
| Saque mínimo | R$500 | Pode aprovar abaixo |
| Tolerância zero | Bloqueio automático em 3 denúncias | Pode reverter bloqueio |
| Valor aula | R$100 | Pode alterar via config |

---

## 5. Autenticação e Segurança

### 5.1 Acesso

- Login com email/senha (Firebase Auth)
- Contas criadas manualmente no Firebase Console (não há cadastro público)
- Custom claim `admin: true` setada via Firebase Admin SDK (ou manualmente)
- `AdminGuard` no GoRouter: verifica `currentUser.role == 'admin'` antes de renderizar qualquer rota `/admin/*`

### 5.2 Regras Firestore

```firestore
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Admin bypass (lê e escreve em tudo)
    function isAdmin() {
      return request.auth != null
        && get(/databases/$(database)/documents/users/$(request.auth.uid)).data.role == 'admin';
    }

    match /{document=**} {
      allow read, write: if isAdmin();
    }
  }
}
```

**⚠️ Cuidado:** Regra global `allow read,write: if isAdmin()` é poderosa demais para produção. Idealmente manter as regras existentes do app (granulares) e adicionar `isAdmin()` como OR em cada coleção.

### 5.3 HTTPS

Obrigatório. Flutter Web requer `https://` para Service Workers e Firebase Auth redirect. Certificado SSL via Let's Encrypt (Certbot).

---

## 6. Stack Técnica e Dependências

### 6.1 O que já existe e será reaproveitado

| Componente | Uso no painel |
|-----------|--------------|
| Firebase Auth | Login do admin (reutilizar `FirebaseAuthService`) |
| Firestore | Todas as queries (reutilizar `FirestoreService`) |
| Riverpod | Estado (reutilizar padrão) |
| GoRouter | Rotas (criar nova árvore `/admin/*`) |
| Widgets compartilhados | `AppButton`, `AppCard`, `AppColors`, `AppTheme` |
| `fl_chart` | (já no pubspec) gráfico dashboard |

### 6.2 O que precisa ser adicionado

| Dependência | Versão | Motivo |
|------------|--------|--------|
| `pluto_grid` (ou `shadcn_flutter`) | — | Tabelas com filtro, ordenação, paginação |
| `csv` | ^1.0.0 | Exportar relatórios |
| `file_saver` | — | Download do CSV no browser |
| `intl` | (já tem) | Formatação data/moeda |

### 6.3 Estrutura de diretórios

```
lib/
├── admin/
│   ├── admin_shell.dart              # Layout base (sidebar + topbar)
│   ├── guards/
│   │   └── admin_guard.dart          # Redireciona se role != admin
│   ├── screens/
│   │   ├── dashboard_screen.dart
│   │   ├── usuarios_list_screen.dart
│   │   ├── usuario_detail_screen.dart
│   │   ├── aulas_list_screen.dart
│   │   ├── aula_detail_screen.dart
│   │   ├── pagamentos_list_screen.dart
│   │   ├── pagamento_detail_screen.dart
│   │   ├── denuncias_list_screen.dart
│   │   ├── denuncia_detail_screen.dart
│   │   ├── financeiro_saques_screen.dart
│   │   ├── extrato_instrutor_screen.dart
│   │   ├── relatorios_screen.dart
│   │   └── configuracoes_screen.dart
│   └── widgets/
│       ├── admin_table.dart          # DataTable padronizada
│       ├── admin_filter_bar.dart     # Barra de filtros
│       ├── stat_card.dart            # Card do dashboard
│       └── admin_chart.dart          # Gráfico genérico
├── presentation/router/
│   └── app_router.dart               # Adicionar rotas /admin/*
```

---

## 7. Requisitos Mínimos de VPS

### 7.1 Premissas

- Flutter Web gera **arquivos estáticos** (HTML+JS+CSS+WASM) — NÃO precisa de servidor Dart
- Qualquer servidor HTTP serve: Nginx, Apache, Caddy
- Firebase é o backend real — a VPS só precisa servir os arquivos e fazer proxy reverso se necessário

### 7.2 Mínimo absoluto

| Item | Mínimo | Recomendado | Motivo |
|------|--------|-------------|--------|
| **CPU** | 1 vCPU | 2 vCPUs | Arquivos estáticos — quase zero de processamento |
| **RAM** | 512 MB | 1 GB | Nginx + SO usam ~200MB |
| **Armazenamento** | 1 GB | 5 GB | Build do Flutter Web ~8MB + assets ~5MB |
| **SO** | Ubuntu 22.04 / Debian 12 | Ubuntu 24.04 LTS | Suporte longo |
| **Rede** | 100 Mbps | 500 Mbps | Tráfego leve (~100 req/dia) |
| **Banda** | 50 GB/mês | 200 GB/mês | Dados majoritariamente texto |
| **Domínio** | 1 (ex: admin.zeyro.app) | 1 | Certificado SSL obrigatório |

### 7.3 Software necessário

| Software | Mínimo | Função |
|----------|--------|--------|
| Nginx | 1.24+ | Servir arquivos estáticos + proxy reverso + SSL |
| Certbot | último | Certificado SSL Let's Encrypt automático |
| git | — | Apenas para deploy inicial (ou rsync) |
| build-essential | — | Apenas se for compilar na VPS (não recomendado) |

### 7.4 Estimativa de custo mensal

| Item | Custo estimado |
|------|---------------|
| VPS (1 vCPU, 1GB) | R$ 20–40/mês (Hetzner, Contabo, DigitalOcean) |
| Domínio .app | R$ 40–60/ano |
| Certificado SSL | Grátis (Let's Encrypt) |
| **Total** | **~R$ 25–50/mês** |

### 7.5 Deploy (CI/CD)

```bash
# 1. Compilar localmente
cd zayro
flutter build web --release --base-href /admin/

# 2. Enviar para VPS
rsync -avz build/web/ user@vps:/var/www/zeyro-admin/

# 3. Nginx config (exemplo)
server {
    listen 443 ssl;
    server_name admin.zeyro.app;

    ssl_certificate /etc/letsencrypt/live/admin.zeyro.app/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/admin.zeyro.app/privkey.pem;

    root /var/www/zeyro-admin;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

**Alternativa mais simples:** Firebase Hosting (grátis no plano Spark) — sem VPS necessária. Se o admin for só 1 pessoa, Firebase Hosting + `firebase deploy --only hosting` resolve sem servidor.

---

## 8. Build e Deploy

### 8.1 Build local

```bash
flutter build web --release --dart-define=FLUTTER_WEB_USE_SKIA=true
```

### 8.2 Opções de deploy

| Opção | Custo | Esforço | Ideal para |
|-------|-------|---------|------------|
| Firebase Hosting | Grátis (Spark) | Mínimo (1 comando) | MVP, 1 admin |
| VPS + Nginx | R$ 20–40/mês | Médio | Produção, controle total |
| Vercel | Grátis (Hobby) | Mínimo | Alternativa sem VPS |
| Cloudflare Pages | Grátis | Mínimo | Alternativa sem VPS |

### 8.3 Pipeline sugerido

```yaml
# .github/workflows/deploy-admin.yml
name: Deploy Admin Panel
on:
  push:
    branches: [dev]
    paths: ['zayro/lib/admin/**', 'zayro/lib/presentation/router/**']
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: subosito/flutter-action@v2
      - run: flutter build web --release
      - run: firebase deploy --only hosting:admin
```

---

## 9. Prioridade de Implementação

| Prio | Funcionalidade | Esforço estimado | Valor | Depende de |
|------|---------------|------------------|-------|------------|
| **P0** | AdminShell + Login + Guard | 2 dias | 🔴 Base para tudo | — |
| **P0** | Dashboard (cards + gráfico) | 2 dias | 🔴 Visão geral | AdminShell |
| **P0** | Denúncias (listar + resolver) | 3 dias | 🔴 Tolerância zero exige | AdminShell |
| **P0** | Usuários (listar + bloquear) | 2 dias | 🔴 Operação básica | AdminShell |
| **P1** | Aulas (listar + cancelar) | 3 dias | 🟡 Gestão de conflitos | AdminShell |
| **P1** | Pagamentos (listar + estornar) | 2 dias | 🟡 Financeiro | AdminShell |
| **P1** | Financeiro (saques + extrato) | 3 dias | 🟡 Instrutores precisam sacar | AdminShell |
| **P2** | Relatórios + CSV | 3 dias | 🔵 Tomada de decisão | AdminShell |
| **P2** | Configurações | 1 dia | 🔵 Autonomia | AdminShell |
| **P2** | Dark mode | 1 dia | 🔵 Qualidade de vida | AdminShell |

**Total estimado:** ~22 dias de desenvolvimento (1 dev full-time).

---

## Anexo A — Fluxo de custom claims (admin)

```dart
// No backend/functions (Node.js):
const admin = require('firebase-admin');
admin.auth().setCustomUserClaims(uid, { admin: true });

// No Flutter:
final user = FirebaseAuth.instance.currentUser;
user?.getIdTokenResult().then((result) {
  final isAdmin = result.claims?['admin'] == true;
});
```

**Alternativa sem backend:** usar `users/{uid}.role == 'admin'` como fonte de verdade (mais simples, sem Cloud Functions).

---

## Anexo B — Documento `config/sistema` no Firestore

```json
{
  "valor_aula": 100.0,
  "aulas_minimas": 2,
  "saque_minimo": 500.0,
  "percentual_plataforma_cancelamento": 25,
  "percentual_instrutor_falta": 25,
  "faq_texto": "…",
  "contato_suporte": "suporte@zayro.app",
  "updated_by": "admin_uid",
  "updated_at": "2026-07-13T00:00:00Z"
}
```
