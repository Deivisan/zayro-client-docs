# Análise do Fluxo do Zayro

**Autor:** Deivison Santana
**Data:** 13 de julho de 2026
**Público:** Cliente — visão executiva do produto

> Documento elaborado a partir da análise dos áudios gravados em 13/07/2026.
> Apresenta o estado atual do aplicativo, o que já está implementado, o que falta
> finalizar (polimentos) e como será o fluxo validado. Toda informação — inclusive
> as pendências — foi deixada explícita para o cliente.

---

## 1. Visão geral

Analisei toda a questão dos áudios que foram lançados e levantei cada um dos
pontos tratados. Organizei abaixo, de forma transparente:

- o que **já existe** no aplicativo;
- o que **falta finalizar** (polimentos e ajustes);
- como **será o fluxo** conforme alinhado.

O objetivo é que todas as informações — inclusive as que ainda estão em aberto —
fiquem evidentes para o cliente.

---

## 2. Cadastro e aprovação do instrutor

**Como será o fluxo**

- O instrutor cria o perfil na plataforma e envia os documentos.
- O perfil fica como **pendente** até a atendente validar e autorizar.
- Por esse motivo inicial, é necessário um **painel administrativo** para
  aprovação manual.
- O **valor das aulas é definido pela plataforma**, não pelo instrutor.

**Status no app:** 🟡 Parcialmente implementado

| Item | Situação |
|------|----------|
| Campo `status` (pendente/aprovado/ativo/suspenso/bloqueado) | ✅ Já existe no modelo |
| Painel administrativo de aprovação | ❌ Falta criar |
| Valor da aula definido pela plataforma | ❌ Falta (hoje não é centralizado) |

---

## 3. Configuração de agenda do instrutor

**Como será o fluxo**

- Após a aprovação, o instrutor configura a agenda:
  - pode **bloquear horários** disponíveis;
  - não pode bloquear uma aula já marcada (para cancelar, usa-se o cancelamento).
- O instrutor deve reservar **um dia da semana para a prova prática no DETRAN**.

**Cancelamento**

A regra de cancelamento do **candidato é a mesma do instrutor**:

- o aluno pode cancelar a aula;
- **até 24 horas** antes do horário marcado: cancelamento **sem custo**
  (estorno integral);
- **fora desse prazo** (menos de 24h de antecedência): incide **multa**, conforme
  a regra de repasse (parte do valor fica com o instrutor e parte com a plataforma).

**Status no app:** 🟡 Parcialmente implementado

| Item | Situação |
|------|----------|
| Reserva de agenda com proteção anti-conflito | ✅ Já existe |
| Reserva semanal do período DETRAN (prova grátis na 1ª vez; paga se faltou ou nas demais) | ❌ Falta |

---

## 4. Ganhos e forma de recebimento

**Como será o fluxo**

- No painel do instrutor, cada horário disponível já mostra o valor que ele ganhará.
- Aparece um **resumo de ganhos** conforme ele abre horários.
- Formas de recebimento: **mensal ou quinzenal**. Não existe pagamento diário nem semanal.
- O instrutor informa o **número da conta bancária** no painel.
- Ele vê:
  - quanto ganharia se fechar toda a agenda;
  - quanto já recebeu até o momento.
- A agenda pode ser configurada para o **mês todo, a semana toda ou por quinzena**.

**Status no app:** 🟡 Parcialmente implementado

| Item | Situação |
|------|----------|
| Modelo de regras financeiras (cancelamento, falta, saldo, saque) | ✅ Já existe |
| Forma de recebimento (quinzenal/mensal) | ❌ Falta vincular ao painel |
| Conta bancária do instrutor | ❌ Falta |
| Resumo de ganhos (potencial da agenda + recebido) | ❌ Falta |

---

## 5. Reserva do dia/horário da prova prática (DETRAN)

**Regras gerais**

- O instrutor define um **período reservado para a prova prática no DETRAN**
  (ex.: das 7h às 9h) e a **data** fica a critério do instrutor.
- A prova prática é **gratuita apenas na primeira vez**.
- Se o candidato **faltou à prova gratuita**, ele **paga** na próxima.
- Nas **demais vezes** (além da 1ª), a prova prática também é **paga**.
- **Nada é obrigatório**: tudo tem disponibilidade; o instrutor controla a
  quantidade de pessoas que podem ser agendadas para cada data, com
  **mínimo de 3 participantes**.

**Gatilho**

- Quando faltam **2 aulas para o término** das aulas contratadas, o candidato
  recebe:

  > Já se sente seguro de marcar sua aula prática?
  > 1 — Sim
  > 2 — Não

**Se SIM**

- Abre a agenda para que ele escolha o dia, a partir dos dias que o instrutor
  reservou na agenda virtual.
- Mensagem com os dias/horas em que o instrutor estará no DETRAN com o veículo:

  > Esses são os dias e horas que seu instrutor estará na DETRAN com o veículo
  > para a realização da prova prática, qual fica melhor para você?
  > [Opção] [Opção] [Opção]

- Após a escolha, mensagem de finalização:

  > 🎉 Sua primeira prova prática é por nossa conta 🎉
  > Agora que você já reservou o dia na agenda do seu instrutor, dirija-se ao
  > DETRAN e realize o seu agendamento por lá.

- Essa agenda segue o **fluxo de cancelamento igual aos outros**: cancelamento
  **gratuito em até 24h**; se cancelar após esse tempo, o próximo agendamento
  será **cobrado**.

**Se NÃO**

- Oferta para comprar mais 2 aulas:

  > O que acha de comprar mais 2 aulas para se sentir mais seguro?

- Em seguida, agenda do instrutor para escolha dos dias e horários para
  **pagamento**.

**Status no app:** 🔴 Não implementado

> ⚠️ Falta: gatilho nas 2 últimas aulas, escolha do dia na agenda do instrutor,
> mensagem de finalização, ramificação "não" (compra de 2 aulas) e controle de
> capacidade (mín. 3 participantes).

---

## 6. Notificações para prova prática

**Como será o fluxo**

- Quando faltam **2 aulas para o término**, o candidato recebe a notificação
  com o prompt _"Já se sente seguro de marcar sua aula prática?"_ (Sim/Não),
  conforme detalhado na seção 5.
- O instrutor recebe uma notificação pedindo que ele solicite ao aluno que
  **reserve o horário** no dia em que o instrutor separou para prova prática.
- O **veículo usado na prova é o do instrutor**.

**Status no app:** 🟡 Parcialmente implementado

| Item | Situação |
|------|----------|
| Infraestrutura de notificações (FCM) | ✅ Já existe |
| Gatilho das notificações de prova (últimas 2 aulas) | ❌ Falta |

---

## 7. Forma de pagamento fixa

**Como será o fluxo**

- Se o pagamento for **fixo**, as únicas opções válidas são:
  - **quinzenal**; ou
  - **mensal**.

**Status no app:** 🔴 Não implementado

> ⚠️ Falta a regra de negócio "pagamento fixo = apenas quinzenal/mensal".

---

## 8. Correções de fluxo e busca (candidato × instrutor)

Com base nos áudios de correção, os seguintes ajustes de UX foram definidos:

### 8.1 Busca não deve ser por disponibilidade do candidato

- As telas atuais onde o candidato busca "dia e horário que tem disponível"
  são irrelevantes.
- A ideia **não é** que o candidato ache no horário que ele quer.
- O candidato deve navegar pela **agenda do instrutor**.

### 8.2 Perfil do instrutor: endereço, não região

- A "região" no perfil do instrutor não é interessante.
- Já está acordado o uso de um **endereço** do local (fácil de achar no Waze).

### 8.3 Categoria e turno

- Categoria **A**, **B** e **A+B** são válidas.
- O "turno preferido" (manhã/tarde/noite) **não pertence à busca do candidato**
  — ele deve ficar no **perfil do instrutor**.
- Se o candidato pedir turno noturno e o instrutor ensina à noite, ele deve
  aparecer (senão o marketing fica fraco).

### 8.4 Cardápio de instrutores por categoria

- Separar: categoria A → um conjunto de instrutores; categoria B → outro.
- Mostrar um **card com o perfil de todos os instrutores da categoria**,
  **sem** a escolha de manhã/tarde/noite.
- Ao clicar no instrutor, aparecem os horários disponíveis dele.
- O candidato **não determina o horário**: quem está no comando é o instrutor,
  que diz "tenho esses horários".

**Status no app:** 🟡 Parcialmente implementado

| Item | Situação |
|------|----------|
| Escolha de datas usa a disponibilidade (DiasTurnos) do instrutor | ✅ Já existe |
| Filtro "Qual turno prefere?" (manhã/tarde/noite) na busca | ⚠️ Deve ser removido |
| Cards de instrutores separados por categoria A/B | ⚠️ Falta refatorar |

---

## 9. Limpeza de telas e padronização

**Como será**

- Remover telas inúteis e renomear telas para seus nomes corretos.
- Eliminar o esquema de "match"/cardápio onde a pessoa escolhia (não existe mais).
- Concluir o fluxo de pagamento com Mercado Pago e ativar as notificações.
- Só então iniciar os testes com usuários reais — o app deve estar pronto e coeso.

**Status no app:** 🟡 Em andamento

> ⚠️ Há telas a remover/renomear conforme alinhamento tela a tela.

---

## 10. Resumo do que falta finalizar

> Todas as pendências abaixo ficam evidentes para o cliente.

| # | Item | Status |
|---|------|--------|
| 1 | Painel administrativo de aprovação do instrutor | 🔴 Faltando |
| 2 | Valor da aula definido pela plataforma | 🔴 Faltando |
| 3 | Reserva semanal do período DETRAN (prova grátis na 1ª vez; paga se faltou ou nas demais) | 🔴 Faltando |
| 4 | Notificações de prova prática (últimas 2 aulas) | 🔴 Faltando |
| 5 | Recebimento (quinzenal/mensal) + conta bancária + resumo de ganhos | 🔴 Faltando |
| 6 | Regra de pagamento fixo = quinzenal/mensal | 🔴 Faltando |
| 7 | Remover filtro "turno prefere" da busca do candidato | 🟡 Refatorar |
| 8 | Separar cards de instrutores por categoria A/B | 🟡 Refatorar |
| 9 | Finalizar fluxo de pagamento (Mercado Pago) | 🟡 Polir |
| 10 | Remover telas inúteis / renomear / remover "match" | 🟡 Refatorar |

**Legenda:** 🟢 Pronto · 🟡 Parcial/Refatorar · 🔴 Faltando

---

## 11. Próximos passos

1. **Concluir o fluxo de pagamento** (Mercado Pago) — etapa já iniciada.
2. **Dar continuidade à lógica financeira** (recebimento e regras definidas).
3. Em seguida, **eliminar telas, renomear e refazer a busca** (instrutor-driven),
   com alinhamento tela a tela.
4. Por fim, **iniciar os testes** com usuários, com o app pronto e consistente.
