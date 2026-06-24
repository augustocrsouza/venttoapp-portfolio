# 🚀 Repositório de Estudos: Backend & Infraestrutura (VenttoApp)

Olá! Meu nome é Cesar e este repositório é uma documentação da arquitetura e das decisões técnicas do meu projeto prático de estudos em desenvolvimento Backend e Infraestrutura.

Para consolidar meus conhecimentos em **Java, Spring Boot e Cloud**, decidi criar um sistema do zero. Como laboratório de estudos, escolhi o cenário de gestão de contratos e eventos. O que começou como uma API de estudos evoluiu e tomou a forma de um SaaS funcional, que hoje chamo de VenttoApp.

Este repositório não contém o código-fonte proprietário da aplicação, mas sim a **documentação da arquitetura, das tecnologias que estudei e de como estruturei o pipeline e a infraestrutura na nuvem.**

## 🛠️ Stack Tecnológica e Decisões de Estudo

Durante o desenvolvimento, foquei em aprender as seguintes ferramentas e conceitos:

### 1. Desenvolvimento da API
* **Linguagem & Framework:** Construí a base do sistema usando **Java** e **Spring Boot**. A tipagem forte e a estrutura rigorosa do framework me ajudaram a entender melhor a organização de regras de negócio e a construção de APIs RESTful.
* **Segurança:** Implementação de autenticação e criptografia de senhas (BCrypt).

### 2. Persistência de Dados e Armazenamento
* **Banco de Dados Relacional:** Utilizei o **PostgreSQL**.
* **Cloud Database:** Configurei o banco para rodar no **AWS RDS**, entendendo como gerenciar um banco de dados hospedado na nuvem.
* **Arquivos Estáticos:** Para não sobrecarregar a aplicação com imagens e PDFs de contratos, estudei a integração com o **AWS S3** para o armazenamento de arquivos.

### 3. Containerização e Deploy (DevOps)
Um dos meus maiores focos foi entender como tirar a aplicação do ambiente local (`localhost`) e colocá-la em produção de forma automatizada:
* **Docker:** Containerização do backend em Spring Boot.
* **CI/CD:** Criação de pipelines com **GitHub Actions** para realizar o build automático da imagem e enviá-la para o **AWS ECR**.
* **Hospedagem:** Deploy da aplicação em uma instância **AWS EC2**, mantendo o frontend e o banco de dados separados do servidor da aplicação.

### 4. Automação e Inteligência Artificial
Para lidar com os e-mails de suporte que o projeto começou a receber, implementei um fluxo de triagem automatizado:
* **Make & Webhooks:** Criação de fluxos para escutar a caixa de entrada do Gmail.
* **LLM (Claude da Anthropic):** Prompt engineering para criar uma máquina de estados onde a IA analisa o e-mail. Se faltam dados, a IA pede ao usuário. Se é um bug real, a IA extrai as informações.
* **Jira API:** Abertura automática de cards de suporte no Jira apenas quando os dados técnicos estão completos.

---
## ⚙️ Operação e Monitoramento Contínuo (Data Observability)

O código-fonte oficial da API do Ventto é mantido em um repositório privado. Um pipeline analítico confiável depende diretamente da saúde e da integridade do ambiente transacional (OLTP) que gera a informação.

Por isso, utilizo a aba **[Issues](https://github.com/augustocrsouza/venttoapp-portfolio/issues/)** deste repositório público como um **Diário de Engenharia (Ops Log)**. É aqui que documento ativamente a minha rotina de estudo para sustentação real do sistema em produção na AWS, garantindo a qualidade do dado na origem.

### 🏷️ Dicionário de Operações (Labels)
Para organizar o histórico de monitoramento e facilitar a leitura da saúde da infraestrutura, utilizo as seguintes classificações nas *Issues*:

* 🔵 **`ops-log` (Health Checks e Rotina):** Registros de auditoria preventiva. Inclui a verificação periódica de uso de disco (EC2), consumo de memória dos contêineres (Docker), estabilidade de conexões do banco de dados (RDS PostgreSQL) e validação de políticas de retenção de backup (Disaster Recovery).
* 🔴 **`incident` (Falhas e Indisponibilidades):** Registro de anomalias reais ocorridas em produção. Documenta quedas de serviço, picos anormais de infraestrutura ou falhas de *deploy* que possam impactar a geração ou integridade dos dados.
* 🟣 **`post-mortem` (Análise de Causa Raiz - RCA):** Documentação técnica detalhada após a resolução de um incidente. Descreve o que falhou, por que falhou (analisando os logs da aplicação) e qual o plano de ação implementado na arquitetura para evitar que o problema volte a corromper o fluxo de informações.

Convido você a explorar o histórico de *Issues* para acompanhar a evolução e a manutenção contínua desta arquitetura.
---
## 🌐 O Projeto em Produção
O que começou como um laboratório de estudos tomou forma e hoje está em produção. Você pode conferir o resultado final da aplicação rodando na nuvem através dos links abaixo:

* **Site Oficial:** [Acesse o VenttoApp](https://www.venttoapp.com.br)
* **Instagram:** [@venttoapp](https://www.instagram.com/venttoapp)

Estou em constante transição e aprofundamento nos estudos de engenharia de dados e desenvolvimento backend. Construir o VenttoApp foi a melhor forma que encontrei de sair da teoria e colocar a mão na massa com problemas reais de infraestrutura, banco de dados e automação.
