# Roadmap Zayro App — Estado Atual, Entregas e Pendências

> Documento operacional atualizado para acompanhar o contrato e a execução real do projeto.  
> Fonte de verdade de produto: `../ZAYRO-MVP-COMPLETO.md`.  
> Fonte de verdade técnica: `../PLANO-REFATORACAO-TELAS.md`.  
> Atualizado em: 09/06/2026.

---

## 1. Visão geral

O **Zayro** é um marketplace nacional de aulas práticas de direção, conectando candidatos à CNH e instrutores práticos autônomos.

O MVP atual não possui IA, match psicológico ou lógica avançada. O foco é:

- cadastro;
- localização;
- categoria A/B/AB;
- lista de instrutores;
- perfil/agenda;
- contratação de aulas;
- pagamento;
- confirmação;
- pós-aula;
- avaliação;
- denúncias;
- regras de crédito e cancelamento.

---

## 2. Status executivo

| Item | Situação atual |
|------|----------------|
| Protótipos HTML | **63 telas** em `app/screens/` |
| Telas Flutter | **63 arquivos de tela** em `zeyro/lib/presentation/screens/` |
| Fluxo visual do MVP | Implementado/prototipado |
| Fluxo funcional real | Parcial, ainda pendente de integrações e testes |
| Firebase | Estrutura presente, validação real em produção ainda pendente |
| Pagamento real | Pendente |
| Testes manuais ponta a ponta | Pendente |
| Produção com público reduzido | Pendente |
| Entrega comercial final | Pendente |

**Resumo:** as fases iniciais de desenvolvimento e prototipação já passaram. O projeto possui base visual, telas e fluxo completo do MVP, mas ainda não deve ser tratado como entregue em produção comercial.

---

## 3. Arquitetura do app

```text
zeyro/lib/
├── core/
│   ├── config/       # Configurações globais
│   ├── constants/    # Constantes do app
│   ├── data/         # Dados estáticos
│   ├── debug/        # Observabilidade local/debug
│   ├── services/     # Serviços centrais
│   ├── theme/        # Design system Flutter
│   └── utils/        # Utilitários
├── data/
│   ├── models/       # Modelos serializáveis
│   └── services/     # Firestore/Auth/Storage e dados auxiliares
├── presentation/
│   ├── providers/    # Riverpod providers
│   ├── router/       # GoRouter
│   ├── screens/      # 63 telas Flutter
│   └── widgets/      # Componentes compartilhados
└── main.dart
```

### Stack

- Flutter 3.41;
- Dart 3.11;
- Firebase Core/Auth/Firestore/Storage;
- Riverpod;
- GoRouter;
- JSON Serializable/Build Runner;
- Google Fonts;
- Google Maps/Flutter Map disponíveis como dependências.

---

## 4. Contagem de telas Flutter

Total atual: **63 telas Dart**.

| Área | Quantidade | Observação |
|------|------------|------------|
| Candidato | 15 | home, cadastro, perfil, onboarding, aulas e pós-aula |
| Contratação | 9 | fluxo crítico de contratação |
| Instrutor | 6 | home, cadastro, perfil, agenda, carteira |
| Autenticação/Chat | 6 | welcome, login, cadastro de role, chat e mensagem |
| Alertas | 7 | alertas operacionais |
| Erros | 13 | telas de erro do MVP |
| Gerais | 7 | splash, settings, suporte, termos, notificações, report, debug |

---

## 5. Telas e funcionalidades já disponíveis/prototipadas

### 5.1 Autenticação e entrada

| Tela | Status |
|------|--------|
| Splash | Implementada |
| Welcome | Implementada |
| Login | Implementada |
| Seleção de papel (candidato/instrutor) | Implementada |
| Cadastro candidato | Implementado/prototipado |
| Cadastro instrutor | Implementado/prototipado |

### 5.2 Onboarding do candidato

| Tela | Status |
|------|--------|
| Situação do candidato | Implementada |
| Localização | Implementada com estados/cidades liberados |
| Categoria A/B/AB | Implementada |

### 5.3 Fluxo de contratação

| Etapa | Tela | Status |
|-------|------|--------|
| 1 | Busca de instrutores | Implementada/prototipada |
| 2 | Instrutores disponíveis | Implementada/prototipada |
| 3 | Perfil detalhado do instrutor | Implementado/prototipado |
| 4 | Quantidade de aulas | Implementada/prototipada |
| 5 | Escolha de datas | Implementada/prototipada |
| 6 | Resumo do pedido | Implementado/prototipado |
| 7 | Aceite de termos | Implementado/prototipado |
| 8 | Pagamento | Implementado/prototipado, integração real pendente |
| 9 | Confirmação de pagamento | Implementada/prototipada |

### 5.4 Candidato e aulas

| Funcionalidade | Status |
|----------------|--------|
| Home candidato | Implementada |
| Perfil candidato | Implementado |
| Editar perfil candidato | Implementado |
| Lista de aulas | Implementada |
| Resumo da aula | Implementado |
| Avaliação de aula | Implementada |
| Detalhe de aula | Implementado |
| Falta registrada | Implementada |
| Contestação | Implementada |

### 5.5 Instrutor

| Funcionalidade | Status |
|----------------|--------|
| Home instrutor | Implementada |
| Agenda instrutor | Implementada/prototipada |
| Carteira instrutor | Implementada/prototipada |
| Perfil instrutor | Implementado |
| Editar perfil instrutor | Implementado |

### 5.6 Comunicação, suporte e segurança

| Funcionalidade | Status |
|----------------|--------|
| Lista de chat | Implementada/prototipada |
| Sala de chat | Implementada/prototipada |
| Nova mensagem | Implementada/prototipada |
| Notificações | Implementadas/prototipadas |
| Suporte | Implementado/prototipado |
| Configurações | Implementadas/prototipadas |
| Termos e privacidade | Implementados/prototipados |
| Denúncia | Implementada/prototipada |

### 5.7 Alertas e erros

| Tipo | Quantidade | Status |
|------|------------|--------|
| Alertas operacionais | 7 | Implementados |
| Erros de fluxo | 13 | Implementados |

Alertas cobertos: cancelamento, falta, conta suspensa, instrutor indisponível, denúncia, crédito e saque.

Erros cobertos: campos obrigatórios, CPF, telefone, e-mail, cidade, horários, horário reservado, pagamento, Pix, conexão, termos, cancelamento e reagendamento.

---

## 6. Dados e regras já incorporados

### 6.1 Categorias

- A — Moto;
- B — Carro;
- AB — Moto e carro.

### 6.2 Valores

- Aula de carro: R$ 100;
- Aula de moto: R$ 100;
- Quantidade mínima: 2 aulas.

### 6.3 Regiões liberadas

Foram incorporados os 9 estados compatíveis com a direção atual do projeto:

- BA;
- CE;
- GO;
- MT;
- PA;
- PR;
- RS;
- SC;
- SP.

Também foram incorporados **2969 municípios** com base em dados do IBGE.

---

## 7. Pendências para app funcional

### 7.1 Integrações reais

- [ ] Pagamento real com gateway definido (Pix/cartão);
- [ ] Validação real de Firebase Auth;
- [ ] Gravação/leitura real dos principais fluxos no Firestore;
- [ ] Upload real de documentos/fotos no Firebase Storage;
- [ ] Regras finais de segurança do Firestore/Storage;
- [ ] Configuração de ambiente de produção.

### 7.2 Testes e homologação

- [ ] Testar cadastro candidato ponta a ponta;
- [ ] Testar cadastro instrutor ponta a ponta;
- [ ] Testar onboarding completo;
- [ ] Testar fluxo de contratação completo;
- [ ] Testar pagamento real/simulado com retorno de status;
- [ ] Testar reserva de agenda apenas após pagamento aprovado;
- [ ] Testar chat/mensagem real;
- [ ] Testar denúncia, contestação e falta;
- [ ] Testar telas de erro;
- [ ] Testar navegação por role;
- [ ] Gerar build Android final.

### 7.3 Operação e lançamento

- [ ] Configurar domínio/ambiente;
- [ ] Configurar contas de produção;
- [ ] Definir gateway de pagamento;
- [ ] Definir política operacional de suporte;
- [ ] Iniciar fase de produção reduzida;
- [ ] Medir estabilidade e custos reais;
- [ ] Corrigir problemas encontrados;
- [ ] Preparar expansão de uso.

---

## 8. Fase de produção reduzida — 1 mês

Após o primeiro deploy funcional, o projeto entrará em **1 mês de testes em produção com público reduzido**.

### Objetivos

- Validar uso real da plataforma;
- Fazer teste de estresse controlado;
- Confirmar estabilidade do Firebase;
- Verificar comportamento do Firestore com dados reais;
- Testar pagamento e reserva de agenda;
- Detectar bugs de navegação;
- Corrigir problemas antes de escalar.

### Critério de saída

A plataforma só deve ser considerada pronta para uso comercial mais amplo após:

- fluxo candidato completo validado;
- fluxo instrutor validado;
- pagamento funcionando;
- ausência de bugs críticos conhecidos;
- custos de infraestrutura observados;
- app Android estável para grupo reduzido.

---

## 9. Roadmap por fase

### Fase 1 — Base visual e fluxo MVP

Status: **concluída/prototipada**.

- Telas principais;
- Design system;
- Fluxo candidato;
- Fluxo instrutor;
- Fluxo contratação;
- Alertas e erros.

### Fase 2 — Integração funcional

Status: **pendente/em andamento**.

- Firebase real;
- Firestore real;
- Auth real;
- Storage real;
- Pagamento real;
- Persistência de pedidos/aulas.

### Fase 3 — Homologação

Status: **pendente**.

- Testes manuais completos;
- Correções de fluxo;
- Ajustes de usabilidade;
- Validação com o cliente.

### Fase 4 — Produção reduzida

Status: **pendente**.

- Deploy controlado;
- Público reduzido;
- Testes de estresse;
- Monitoramento de custos;
- Correções críticas.

### Fase 5 — Entrega funcional

Status: **pendente**.

- Build Android final;
- Entrega para uso do cliente;
- Início de 30 dias de garantia técnica;
- Planejamento de manutenção mensal.

### Fase 6 — Manutenção mensal

Status: **futura**.

- R$ 200/mês após garantia;
- Correções técnicas;
- Pequenos ajustes;
- Funcionalidades novas somente por acordo/contrato separado.

---

## 10. Itens fora do MVP atual

Não fazem parte do MVP atual:

- Inteligência artificial;
- Match psicológico;
- Onboarding emocional;
- Perfil comportamental complexo;
- Distribuição automática avançada;
- Categorias C, D e E;
- Mudança ou adição de categoria;
- Bonificações complexas;
- Backoffice administrativo completo;
- Expansão comercial sem teste reduzido.

---

## 11. Critérios de aceite para entrega funcional

O app será considerado funcional quando:

- candidato conseguir se cadastrar;
- candidato informar situação, cidade/estado e categoria;
- candidato conseguir visualizar instrutores;
- candidato conseguir abrir perfil/agenda;
- candidato conseguir escolher quantidade mínima de 2 aulas;
- candidato conseguir selecionar datas/horários;
- candidato conseguir revisar resumo;
- candidato conseguir aceitar termos;
- pagamento for processado ou simulado conforme gateway definido;
- confirmação final for exibida;
- instrutor conseguir visualizar agenda básica;
- erros críticos forem tratados;
- build Android for gerado;
- app passar por teste de público reduzido.

---

## 12. Resumo comercial vinculado

- Desenvolvimento contratado: **R$ 3.000,00**;
- Valor já pago: **R$ 200,00**;
- Entrada restante: **R$ 1.000,00**;
- Segunda parcela: **R$ 900,00**;
- Terceira parcela: **R$ 900,00**;
- Primeiro mês de garantia técnica: **sem cobrança adicional**;
- Manutenção após garantia: **R$ 200,00/mês**;
- Código-fonte: **propriedade da DeiviTech / Deivison de Lima Santana**;
- Entrega ao cliente: **aplicativo Android funcional**, não cessão do código-fonte.

---

## 13. Observação final

Este roadmap representa o estado real atual: o projeto possui estrutura, telas e fluxo de MVP avançados, mas ainda precisa de integração, testes, produção reduzida e estabilização antes de ser tratado como produto final entregue para operação comercial ampla.
