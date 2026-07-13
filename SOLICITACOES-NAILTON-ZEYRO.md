# 📋 Modificações Solicitadas — Nailton

> **Data:** 13/07/2026
> **Produto:** Zeyro
> **Fonte:** 6 áudios WhatsApp transcritos via GROQ Whisper
> **Status:** ⏳ Aguardando validação do Nailton

---

## 1. 🧑‍🏫 Cadastro do Instrutor — Simplificação

| O que mudar | Detalhe |
|-------------|---------|
| **Remover** | Todos os campos do cadastro do instrutor, exceto: biografia, foto e disponibilidade |
| **Manter** | ✅ Foto de perfil (obrigatório — "precisa ter uma imagem pra ver ele") |
| **Manter** | ✅ Biografia |
| **Manter** | ✅ Configuração de agenda |
| **Remover** | ❌ Perfil competitivo entre instrutores — "não tem que botar um perfil competitivo entre eles" |
| **Observação** | A parte do veículo com documento enviado **ficou boa** (manter como está) |

> 🎯 **Objetivo:** Simplificar o cadastro para onboard mais rápido de instrutores.

---

## 2. 📅 Agenda do Instrutor — Ajuste Fino

### ❌ Modelo Atual (errado)
```
[Segunda] [Terça] [Quarta] ... [Domingo]
  ↳ Turnos: [Manhã] [Tarde] [Noite]
```

### ✅ Modelo Novo (hora em hora)
Cada dia da semana com slots de **50 minutos**:

| Slot | Horário |
|------|---------|
| 1º | 07:00 — 07:50 |
| 2º | 08:00 — 08:50 |
| 3º | 09:00 — 09:50 |
| 4º | 10:00 — 10:50 |
| 5º | 11:00 — 11:50 |
| 6º | 12:00 — 12:50 |
| 7º | 13:00 — 13:50 |

- O instrutor **configura uma vez** e **replica** para todos os dias da semana
- ⚠️ **"É a agenda completa, ajuste fino que tem que fazer. Essa parte é importante."**

> 🎯 **Motivo:** "A gente vai vender essa hora para o candidato" — precisa ser hora exata, não turno vago.

---

## 3. 🚗 Veículo — Ajustes

| Campo | Especificação |
|-------|---------------|
| Tipo | 🔘 Própria / Alugada (moto ou carro) |
| Remover | ❌ "Carro do aluno" — **não existe essa modalidade** |
| Modelo | 📝 Texto livre |
| Ano | 📅 Filtro: **mínimo 10 anos** (2026 → aceita ≥ 2016) |
| Documento | 📎 Obrigatório: documento do veículo |
| Foto | 🖼️ Foto do veículo ou documento do perfil |

> 🎯 **Regra de ano:** Veículo fabricado **depois de 2016** (sistema não aceita mais que 10 anos).

---

## 4. ❌ Cancelamento do Instrutor — Sem Punição Financeira

### Regra
| Situação | Ação |
|----------|------|
| Instrutor cancela | ❌ **Sem punição financeira** (ele não recebeu nada, não tem o que punir) |
| Cancelamento < 24h | 📝 **Registrar no perfil interno** do instrutor |
| Histórico | 📊 **Computar todos os cancelamentos** — visível no painel administrativo |

> 🗣️ "Quem tem que ver essa questão de ele estar cancelando é o atendimento. Então tem que ficar no perfil dele esses cancelamentos. Quantas aulas ele cancela, tem que ficar computado e aparecendo no painel."

---

## 5. ⭐ Avaliações — Perfil Interno

- Avaliações feitas pelos **alunos após a aula** vão para o **perfil interno** do instrutor
- Não é público — é para **avaliação interna** da plataforma
- Ajuda a **perceber como é esse profissional**

> 🗣️ "Assim como as avaliações que os alunos vão fazer após a aula, todas essas vão para o perfil, mas no perfil interno, para a gente perceber como é esse profissional."

---

## 6. 🏷️ Código Promocional

| Funcionalidade | Descrição |
|----------------|-----------|
| Código no perfil do instrutor | Cada instrutor tem um **código promocional único** |
| Parcerias com influenciadores | Influenciador divulga o código → **mede conversão** |
| Promoções próprias | A plataforma pode criar **códigos promocionais próprios** |
| Métrica | Saber **quantas pessoas estão vindo** através de cada código |

> 🗣️ "Quando eu fizer parceria com alguma influência, aí eu dou o código a ele... para a gente medir quantas pessoas estão vindo através dele."

---

## 📊 Resumo Visual

| # | Mudança | Prioridade | Complexidade |
|---|---------|------------|--------------|
| 1 | Simplificar cadastro instrutor | 🔴 Alta | 🟢 Fácil |
| 2 | Agenda hora em hora (7 slots de 50min) | 🔴 Alta | 🟡 Média |
| 3 | Veículo: filtro 10 anos + remover "carro do aluno" | 🟡 Média | 🟢 Fácil |
| 4 | Cancelamento instrutor: histórico sem punição financeira | 🟡 Média | 🟡 Média |
| 5 | Avaliações no perfil interno do instrutor | 🟢 Baixa | 🟢 Fácil |
| 6 | Código promocional por instrutor | 🟢 Baixa | 🟡 Média |

---

> **Próximo passo:** Aguardando Nailton validar cada item acima. Após validação, implementamos.
