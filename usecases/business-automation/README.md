# 🥇 Automação de Negócios - Insights Competitivos

<!--![image](https://github.ibm.com/skol/agentic-ai-client-bootcamp/assets/451557/b9fb42fc-4aa1-4010-b850-5c8f20e3e05a)-->
![image](assets/hypercar3.png)

## 🤔 O Problema

O departamento de vendas da ABC Motors Corp enfrentava desafios na preparação de propostas de vendas para sua nova linha de veículos de alto desempenho. Sempre que lançam um novo modelo, a equipe de análise competitiva gasta muito tempo e recursos para fornecer seus insights. Os problemas incluem:

- Pesquisas manuais atrasam decisões e reduzem a produtividade.
- Posicionamento fraco prejudica a diferenciação nas vendas.
- Resposta lenta às mudanças de mercado devido à falta de inteligência em tempo real.

## 🎯 Objetivo

A ABC Motors Corp planeja implementar um Sistema de Inteligência Competitiva com IA para automatizar a pesquisa de mercado e a análise de concorrentes. Este sistema ajudará as equipes de vendas a identificar e posicionar rapidamente seus produtos frente aos concorrentes, superando as ineficiências da pesquisa manual e dos insights desatualizados. O objetivo é criar um sistema habilitado por IA que apoie a análise competitiva e a pesquisa de mercado através de:

* Extração de produtos do catálogo de produtos da empresa.
* Identificação e extração dos principais recursos de cada produto.
* Pesquisa de produtos concorrentes com base em atributos-chave.
* Geração de uma tabela de comparação competitiva estruturada com preço, recursos e diferenciais.
* Realização de Análise SWOT (Forças, Fraquezas, Oportunidades e Ameaças) para fornecer insights estratégicos mais profundos.

Ao automatizar essas tarefas, a empresa pretende acelerar os processos de vendas, melhorar a precisão dos dados e permitir que as equipes de vendas tomem decisões informadas mais rapidamente.

## 📈 Valor para o Negócio

* Redução no tempo de pesquisa manual da concorrência.
* Atualizações automatizadas e em tempo real sobre a concorrência no mercado.
* Melhora na eficácia do discurso de vendas.

## 🏛 Arquitetura

Para agilizar o processo de análise competitiva, projetamos um Sistema de Automação Multi-Agente de IA que extrai e analisa autonomamente os dados dos produtos a partir do [Catálogo de Produtos da ABC Motors Corp](../../anexos/businessautomation/ABC_Motor_Product_Catalog_ptbr.pdf). Este sistema adota uma abordagem colaborativa de múltiplos agentes, garantindo eficiência, precisão e insights em tempo real para as equipes de vendas e estratégia. A arquitetura consiste em agentes de IA especializados trabalhando juntos para executar funções principais:

  * Extração de produtos do catálogo de produtos.
  * Extração das características dos produtos a partir do catálogo.
  * Pesquisa de produtos concorrentes.
  * Geração de uma tabela de comparação competitiva estruturada.
  * Análise SWOT (Forças, Fraquezas, Oportunidades e Ameaças).

Este sistema aproveita o poder combinado de um agente do watsonx Orchestrate e de um agente do watsonx.ai, trabalhando juntos de forma integrada para automatizar a pesquisa competitiva, fortalecer os discursos de vendas e minimizar o esforço manual.

<img width="900" alt="image" src="assets/Business_Automation_Architecture.png">

Este caso de uso utiliza as capacidades de um agente do watsonx Orchestrate para extrair informações específicas dos produtos (como nomes e características) do catálogo de produtos e realizar comparações de produtos. Esses agentes são apoiados por um agente especializado desenvolvido no Agent Lab do watsonx.ai, e todos estão integrados dentro do watsonx Orchestrate. Por meio do assistente de chat do watsonx Orchestrate, os agentes colaboram
