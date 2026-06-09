# CONTRATO DE PRESTAÇÃO DE SERVIÇOS DE DESENVOLVIMENTO DE SOFTWARE

## Partes

### Contratada

**DeiviTech** — empresa de desenvolvimento de software, inscrita no CNPJ sob nº **54.910.501/0001-34**, representada por **Deivison de Lima Santana**, e-mail **deivitechfsa@gmail.com**, WhatsApp/Pix **75 98123-1019**, doravante denominada **CONTRATADA**.

### Contratante

**Nailton Reis**, CPF/CNPJ: __________________________________________, doravante denominado **CONTRATANTE**.

Este documento estabelece as condições comerciais, técnicas e operacionais para desenvolvimento do aplicativo **Zayro**, marketplace de aulas práticas de direção.

---

## 1. Objeto

### 1.1 Escopo principal

A CONTRATADA prestará serviço de desenvolvimento do aplicativo **Zayro**, plataforma de conexão entre candidatos à CNH e instrutores práticos de direção, utilizando:

- Aplicativo mobile em **Flutter 3.41 + Dart 3.11**;
- Backend e infraestrutura em **Firebase**;
- Banco de dados **Cloud Firestore**;
- Autenticação via **Firebase Authentication**;
- Armazenamento via **Firebase Storage**;
- Roteamento com **GoRouter**;
- Gerenciamento de estado com **Riverpod**;
- Design system próprio da plataforma.

### 1.2 Estado atual do projeto

As fases iniciais de desenvolvimento já foram executadas. Até o momento, a CONTRATADA entregou ao CONTRATANTE os **protótipos de telas e o desenho visual/funcional do fluxo**, para que o CONTRATANTE possa verificar como o aplicativo ficará.

O aplicativo **ainda não está em versão final funcional**, não foi entregue oficialmente para operação comercial e ainda possui etapas pendentes de integração, testes e produção.

### 1.3 Entrega prevista

A entrega contratada corresponde a um **aplicativo Android funcional**, com fluxo operacional do MVP, disponibilizado para uso e validação do CONTRATANTE após conclusão das etapas pendentes.

O código-fonte não será transferido ao CONTRATANTE. A entrega ao CONTRATANTE é o **aplicativo Android funcional**, e não a propriedade do código-fonte.

---

## 2. Roadmap técnico e entregáveis

### 2.1 Já implementado / prototipado

Foram implementados ou prototipados os seguintes blocos:

| Bloco | Descrição | Status |
|------|-----------|--------|
| Onboarding | Situação do candidato, localização e categoria | Implementado/prototipado |
| Cadastro | Cadastro de candidato e instrutor | Implementado/prototipado |
| Contratação | Busca de instrutor, seleção, quantidade de aulas, datas, resumo, termos, pagamento e confirmação | Implementado/prototipado |
| Instrutores | Lista, perfil, agenda e perfil detalhado | Implementado/prototipado |
| Aulas | Lista, resumo, detalhe, avaliação, falta e contestação | Implementado/prototipado |
| Comunicação | Lista de chat, sala de chat e nova mensagem | Implementado/prototipado |
| Segurança | Denúncias, alertas e telas de erro | Implementado/prototipado |
| Dados regionais | 9 estados liberados e 2969 municípios | Implementado/prototipado |

### 2.2 Ainda pendente para entrega funcional

Permanecem pendentes, para conclusão do aplicativo funcional:

- Integração real de pagamentos (Pix/cartão via gateway a definir);
- Validação completa do fluxo real com Firebase em produção;
- Testes manuais de navegação ponta a ponta;
- Testes de autenticação real;
- Ajustes finais de usabilidade;
- Build Android final;
- Deploy/produção controlada;
- Fase de teste com público reduzido;
- Correções após testes em ambiente real.

### 2.3 Fase de teste em produção reduzida

Após o primeiro deploy funcional, haverá uma fase de **1 (um) mês de testes em produção com público reduzido**, com objetivo de:

- Validar o funcionamento real da plataforma;
- Fazer testes de estresse controlados;
- Identificar falhas de fluxo;
- Medir estabilidade do Firebase/Firestore;
- Corrigir bugs críticos antes de expansão de uso;
- Ajustar regras operacionais com base no uso real.

Esta fase não caracteriza entrega comercial ampla. Trata-se de uma etapa técnica de validação e estabilização.

---

## 3. Valor e forma de pagamento

### 3.1 Valor total do desenvolvimento

O valor total do desenvolvimento contratado é de **R$ 3.000,00 (três mil reais)**.

### 3.2 Valor já pago

O CONTRATANTE já efetuou o pagamento de **R$ 200,00 (duzentos reais)**, referente a custos iniciais e início da execução técnica.

### 3.3 Parcelamento

| Parcela | Percentual | Valor | Situação / vencimento |
|---------|------------|-------|-----------------------|
| Entrada | 40% | **R$ 1.200,00** | R$ 200,00 já pagos + **R$ 1.000,00 a pagar** |
| Segunda parcela | 30% | **R$ 900,00** | Após avanço da integração funcional e ambiente de produção |
| Terceira parcela | 30% | **R$ 900,00** | Na homologação e entrega funcional do aplicativo Android |
| Total | 100% | **R$ 3.000,00** | Valor total contratado |

### 3.4 Forma de pagamento

- **Pix:** 75 98123-1019;
- Ou outro meio previamente acordado entre as partes.

---

## 4. Manutenção, garantia e intervenções futuras

### 4.1 Primeiro mês de garantia técnica

Após a entrega funcional do aplicativo Android, a CONTRATADA prestará **30 (trinta) dias de manutenção corretiva sem cobrança adicional**, como garantia técnica inicial.

Esta garantia cobre apenas:

- Correção de bugs críticos;
- Correção de falhas que impeçam o uso do fluxo principal;
- Ajustes necessários para estabilização após entrega.

Não estão incluídos neste período gratuito:

- Novas funcionalidades;
- Mudanças de escopo;
- Redesign de telas já aprovadas;
- Integrações novas não previstas;
- Alterações solicitadas por mudança de regra de negócio.

### 4.2 Manutenção mensal após a garantia

Após os 30 dias iniciais de garantia, a manutenção será cobrada no valor de **R$ 200,00 (duzentos reais) por mês**.

Esse valor permite que a CONTRATADA mantenha o código, acompanhe falhas, corrija bugs e realize pequenos ajustes técnicos durante o mês contratado.

### 4.3 Intervenções e novas funcionalidades

Intervenções pontuais, melhorias maiores ou novas funcionalidades poderão ser cobradas a partir de **R$ 200,00 por intervenção**, ou formalizadas em contrato/proposta separada quando envolverem escopo maior.

Funcionalidades novas devem ser previamente acordadas entre as partes antes de qualquer implementação.

---

## 5. Propriedade do código-fonte

### 5.1 Titularidade

O código-fonte, arquitetura, estrutura técnica, repositório, componentes reutilizáveis, serviços e lógica de implementação pertencem à **DeiviTech / Deivison de Lima Santana**.

O CONTRATANTE recebe o aplicativo Android funcional para uso dentro do escopo contratado, mas não recebe cessão, venda ou transferência do código-fonte.

### 5.2 Rescisão ou quebra de contrato

Em caso de quebra de contrato, inadimplência ou rescisão pelo CONTRATANTE, fica estabelecido que:

- O código-fonte permanece integralmente sob propriedade da CONTRATADA;
- A CONTRATADA poderá suspender desenvolvimento, manutenção, deploy, acesso técnico e operação vinculada à sua infraestrutura;
- O CONTRATANTE manterá apenas o que já tiver recebido como aplicativo Android/protótipo/apresentação, conforme estágio do projeto no momento da rescisão;
- Não haverá obrigação de entrega do código-fonte.

### 5.3 Valor técnico de instância e código

As partes reconhecem que a infraestrutura em operação, a instância Firebase mantida pela CONTRATADA, a arquitetura técnica e o código já desenvolvido possuem valor técnico estimado de **R$ 13.000,00 (treze mil reais)**.

Esse valor representa a base técnica, a estrutura de execução e o aplicativo Android produzido/operado pela CONTRATADA, não significando transferência automática de propriedade ao CONTRATANTE.

---

## 6. Obrigações da contratada

A CONTRATADA se obriga a:

- Dar continuidade ao desenvolvimento conforme escopo acordado;
- Manter boas práticas de programação e organização do projeto;
- Entregar o aplicativo Android funcional ao final das etapas pendentes;
- Executar a fase de testes em produção reduzida;
- Corrigir bugs críticos durante o primeiro mês de garantia;
- Informar limitações técnicas ou dependências externas relevantes.

---

## 7. Obrigações do contratante

O CONTRATANTE se obriga a:

- Efetuar os pagamentos nos prazos acordados;
- Fornecer informações necessárias para configuração de contas, domínio, Firebase, gateway de pagamento e demais serviços;
- Validar telas, fluxos e decisões de produto em prazo razoável;
- Arcar com custos externos da plataforma, quando existirem;
- Não reivindicar propriedade sobre código-fonte, repositório ou estrutura técnica da CONTRATADA.

---

## 8. Custos externos e infraestrutura

Custos com Firebase, Google Cloud, domínio, gateway de pagamento, APIs, Play Store, serviços de mapa, SMS, e-mail ou quaisquer terceiros não estão incluídos no valor de desenvolvimento, salvo se expressamente acordado por escrito.

Esses custos são de responsabilidade do CONTRATANTE quando necessários para operação comercial da plataforma.

---

## 9. Escopo não incluído no MVP

Não fazem parte do escopo atual:

- Inteligência artificial;
- Match psicológico;
- Onboarding emocional;
- Perfil comportamental complexo;
- Distribuição automática avançada;
- Categorias C, D e E;
- Mudança ou adição de categoria;
- Bonificações complexas;
- Backoffice administrativo completo, salvo proposta separada;
- Publicação ampla com usuários ilimitados sem fase de teste.

---

## 10. Rescisão

Caso o CONTRATANTE deseje rescindir o contrato antes da conclusão:

- Os valores já pagos não serão devolvidos, pois correspondem a trabalho técnico já executado;
- A CONTRATADA não terá obrigação de entregar código-fonte;
- A CONTRATADA poderá interromper infraestrutura, deploy e manutenção;
- O CONTRATANTE receberá apenas o estado do aplicativo Android/protótipo disponível no momento, se tecnicamente possível.

Caso a rescisão ocorra por inadimplência superior a **15 (quinze) dias corridos**, a CONTRATADA poderá suspender imediatamente a continuidade do desenvolvimento e demais acessos técnicos.

---

## 11. Confidencialidade

As partes se comprometem a manter sigilo sobre:

- Informações técnicas do projeto;
- Estratégias comerciais;
- Dados de usuários e instrutores;
- Informações financeiras;
- Qualquer dado sensível tratado durante a execução.

---

## 12. Foro

Fica eleito o foro da comarca de **Feira de Santana — BA** para dirimir eventuais controvérsias decorrentes deste contrato.

---

## 13. Aceite

O aceite deste contrato poderá ocorrer por confirmação escrita em WhatsApp, e-mail, mensagem digital, pagamento da parcela de entrada ou qualquer manifestação inequívoca de concordância do CONTRATANTE.

Não é exigida assinatura física para início ou continuidade da prestação dos serviços.

---

> **Versão:** 2.0 — Atualizado em 09/06/2026  
> **Contratada:** DeiviTech — CNPJ 54.910.501/0001-34  
> **Representante:** Deivison de Lima Santana  
> **Contato:** deivitechfsa@gmail.com — 75 98123-1019  
> **Projeto:** Zayro — Marketplace de Aulas Práticas de Direção
