# CONTRATO DE PRESTAÇÃO DE SERVIÇOS DE DESENVOLVIMENTO DE SOFTWARE

## Partes

### Contratada

**DeiviTech** — empresa de desenvolvimento de software, inscrita no CNPJ sob nº **54.910.501/0001-34**, representada por **Deivison de Lima Santana**, e-mail **deivitechfsa@gmail.com**, WhatsApp/Pix **75 98123-1019**, doravante denominada **CONTRATADA**.

### Contratante

**Naira Ita Nels**, CPF/CNPJ: __________________________________________, doravante denominado **CONTRATANTE**.

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

O código-fonte permanece restrito à CONTRATADA até a quitação integral do contrato. Após a quitação total e a efetiva entrega prevista nas cláusulas 5.3 e 5.5, o código-fonte e os ativos operacionais passam a pertencer integral e exclusivamente ao CONTRATANTE, com o projeto Zayro idealizado por ele.

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

## 5. PROPRIEDADE DO CÓDIGO-FONTE E TITULARIDADE DO PROJETO

### 5.1 Titularidade do projeto e concepção

As partes reconhecem que o aplicativo Zayro foi concebido e idealizado pelo CONTRATANTE, que definiu seu modelo de negócio, fluxos operacionais, regras de funcionamento, funcionalidades, estratégias comerciais e demais elementos conceituais que compõem a plataforma.

A CONTRATADA atua na condição de prestadora de serviços técnicos especializados, sendo responsável pela implementação tecnológica, programação, arquitetura do sistema, estruturação do banco de dados, integrações e demais atividades necessárias para transformar a concepção do CONTRATANTE em aplicativo funcional.

A propriedade da marca Zayro, do modelo de negócio, dos fluxos operacionais, das regras de negócio, da base de usuários, dos dados gerados pela operação e dos demais ativos econômicos e comerciais vinculados ao projeto pertence exclusivamente ao CONTRATANTE.

As partes reconhecem suas respectivas contribuições para o projeto Zayro, cabendo ao CONTRATANTE a idealização e concepção do negócio e à CONTRATADA a implementação técnica da solução tecnológica.

### 5.2 Guarda e titularidade do código-fonte até a quitação total

Durante a vigência desta relação contratual e até a quitação integral do valor contratado, o código-fonte, arquitetura, estrutura técnica, repositório, componentes reutilizáveis, serviços e lógica de implementação permanecem sob guarda, administração e propriedade da CONTRATADA, na qualidade de responsável pelo desenvolvimento e implementação técnica do sistema.

O código-fonte permanecerá restrito à CONTRATADA até a quitação integral do contrato. O CONTRATANTE não terá acesso ao código-fonte durante esse período, salvo nas hipóteses expressamente previstas nas cláusulas 5.4 e 5.5.

A entrega contratada ao CONTRATANTE, até a quitação integral, corresponde ao aplicativo Android funcional para utilização dentro do escopo definido neste contrato, não incluindo cessão, venda, transferência ou acesso ao código-fonte.

### 5.3 Transferência do código-fonte mediante quitação total

Uma vez efetuada a quitação integral do valor contratado (R$ 3.000,00), bem como de quaisquer valores adicionais formalmente contratados entre as partes, a CONTRATADA obriga-se a entregar ao CONTRATANTE o código-fonte completo e atualizado do projeto, juntamente com todos os arquivos, configurações, exportações de dados, scripts e informações técnicas necessárias à replicação e continuidade operacional da plataforma.

A partir da quitação integral e da efetiva entrega dos elementos previstos nesta cláusula, o código-fonte passará a pertencer ao CONTRATANTE para fins de continuidade, manutenção, evolução e gestão do projeto Zayro, permanecendo reconhecida a contribuição técnica da CONTRATADA como desenvolvedora responsável pela implementação da solução.

A entrega deverá ocorrer de forma organizada e cooperativa, garantindo a continuidade do funcionamento do aplicativo sem prejuízo aos usuários e à operação do CONTRATANTE.

A CONTRATADA fornecerá ao CONTRATANTE o código-fonte, os arquivos de projeto, as exportações do banco de dados, as configurações de ambiente (sem credenciais ativas), a documentação técnica disponível e um guia detalhado de implantação, de modo que o CONTRATANTE possa criar e administrar sua própria infraestrutura de forma independente, incluindo a criação de novos projetos no Firebase e demais serviços, sem depender das contas ou credenciais utilizadas pela CONTRATADA durante o desenvolvimento.

### 5.3.1 Transferência e titularidade dos ativos operacionais

Após a quitação integral do valor contratado e de quaisquer valores adicionais eventualmente devidos, a CONTRATADA compromete-se a realizar, sem ônus adicional, a transferência adequada das informações, configurações e dados necessários para que o CONTRATANTE possa constituir sua própria infraestrutura operacional do projeto Zayro de forma independente.

A CONTRATADA fornecerá todas as exportações de dados, configurações de ambiente, estrutura do banco de dados, regras de segurança, integrações documentadas e demais informações técnicas, de modo que o CONTRATANTE possa criar e assumir a titularidade de seus próprios projetos e contas nos serviços utilizados (Firebase, domínios, gateway de pagamento, e-mail transacional e demais serviços necessários à operação da plataforma), sem que isso implique a transferência direta das contas ou credenciais atualmente utilizadas pela CONTRATADA.

A CONTRATADA não fornecerá contas de publicação na Google Play Store, Google Play Console ou demais lojas de aplicativos. A responsabilidade pela criação, titularidade e custos de qualquer conta de publicação é exclusivamente do CONTRATANTE.

O CONTRATANTE será responsável por criar as novas contas e projetos em seu próprio nome. A CONTRATADA prestará orientação técnica e suporte razoável durante o processo de migração e replicação da infraestrutura, limitado ao período de entrega e quitação.

As partes reconhecem que, após a quitação integral, a titularidade plena do projeto Zayro, do código-fonte e da infraestrutura operacional deverá estar em nome do CONTRATANTE, garantindo a continuidade do negócio independentemente da manutenção futura da relação contratual entre as partes.

### 5.4 Rescisão ou encerramento antes da quitação total

Em caso de quebra contratual, inadimplência ou rescisão promovida pelo CONTRATANTE antes da quitação integral do contrato, fica estabelecido que:

I – o código-fonte permanecerá sob propriedade e controle exclusivo da CONTRATADA;

II – a CONTRATADA poderá suspender o desenvolvimento, manutenção, implantação e suporte técnico relacionados ao projeto;

III – o CONTRATANTE manterá apenas os materiais, protótipos, versões e entregas efetivamente disponibilizados até a data da rescisão;

IV – não haverá obrigação de entrega do código-fonte antes da quitação integral do contrato.

Caso a rescisão ocorra após a quitação integral dos serviços contratados, aplicar-se-ão as disposições previstas nas cláusulas 5.3 e 5.5.

### 5.5 Continuidade operacional e contingência

Caso a relação contratual seja encerrada por qualquer das partes após a quitação integral, ou em caso de encerramento das atividades da CONTRATADA, incapacidade de prestação dos serviços, impossibilidade de continuidade do suporte técnico ou descontinuidade definitiva das operações da CONTRATADA, esta disponibilizará ao CONTRATANTE ou ao profissional por ele indicado a versão mais recente do código-fonte, juntamente com as exportações de dados, configurações, documentação técnica e orientações necessárias à continuidade, manutenção e evolução da plataforma.

Esta disposição tem por finalidade assegurar a continuidade operacional do projeto Zayro e não representa obrigação de entrega antecipada do código-fonte durante a vigência normal da parceria ou antes da quitação integral das obrigações financeiras assumidas pelo CONTRATANTE.

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
- Não reivindicar propriedade ou acesso ao código-fonte, repositório ou estrutura técnica da CONTRATADA enquanto não houver quitação total do projeto, conforme cláusulas 5.2 e 5.3.

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
- A CONTRATADA não terá obrigação de entregar código-fonte enquanto não houver quitação total do projeto, exceto nas hipóteses extremas previstas na cláusula 5.5;
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

> **Versão:** 2.5 — Atualizado em 15/06/2026  
> **Contratada:** DeiviTech — CNPJ 54.910.501/0001-34  
> **Representante:** Deivison de Lima Santana  
> **Contato:** deivitechfsa@gmail.com — 75 98123-1019  
> **Projeto:** Zayro — Marketplace de Aulas Práticas de Direção
