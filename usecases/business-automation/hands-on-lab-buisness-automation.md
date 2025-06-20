# 👨🏻‍💻 Use case: Business Automation   

## Table of Contents
- [Architecture](#-architecture)
- [Use Case Description](#use-case-description)
- [Pre-requisites](#pre-requisites)
- [Agent Lab - watsonx.ai](#agent-lab---watsonxai)
  - [Comparison Agent](#comparison-agent)
    - [Setup](#setup)
    - [Configuration](#configuration)
    - [Tools](#tools)
    - [Saving and Deploying](#saving-and-deploying)
- [Integrating watsonx.ai's agent as an External Agent in watsonx Orchestrate](#integrating-watsonxais-agent-as-an-external-agent-in-watsonx-orchestrate)
- [Orchestrate Agent](#orchestrate-agent)
  - [Product Agent](#product-agent)
- [Experience Agents in Action](#experience-agents-in-action)


## 🏛 Architecture  

<img width="900" alt="image" src="assets/Business_Automation_Architecture.png">

## Use Case Description

The sales department of ABC Motor Corp, an automotive large player, when preparing sales proposals, they were spending a lot of time understanding the features of competing products and comparing them with their own products. ABC Motor Corp, needs an automated competitive analysis system to help their sales teams quickly identify and position their products against competitors. Traditionally, gathering competitor insights required extensive manual research, making it inefficient and prone to outdated information. Therefore, the goal of this use case is to create an AI enabled system that support the customer's competitive analysis and market research.

## Pre-requisites

- Check with your instructor to make sure **all systems** are up and running before you continue.
- Please go the through the [environment-setup](/environment-setup) guide for steps on API key creation, project setup, and related configurations.
- If you're an instructor running this lab, check the **Instructor's guides** to set up all environments and systems.

## Agent Lab - watsonx.ai

>**Note:** Before starting the Agent creation, ensure you have generated your API key of watsonx.ai instance. 

We will create one agent **Comparison Agent** in watsonx.ai's Agent Lab as part of this setup:  

From the Home page of Agent Lab, click on the Build an AI agent to automate tasks

![Home page](assets/agent_lab_home.png) 

Let's start the **Comparison Agent**. 

### Comparison Agent  
#### Setup  
1. Enter a **name** for the agent as shown in the image.
2. Add a **description** (optional).
```
The agent compares the given data with additional information gathered from Google search results.
```
![Setup](assets/config_CA.png)  

#### Configuration    
1. Choose **LangGraph** as the framework.  
2. Select **ReAct** as the architecture. 
3. Enter the **Instructions** as shown in the image. These instructions guide your agent on what tasks it should perform. You can use below prompt for it.
```
You are an expert of automobile industry combining given details present in your context window.  Your task is crawl and search the Top 3 product URLs (strictly from the automobile industry) and to analyse and compare products on the following features strictly: Range, Pricing, Acceleration, Top Speed, Interior and Safety Features If a feature is not applicable, mark it as N/A. Additionally, perform a SWOT analysis of top products (Strengths, Weaknesses, Opportunities, and Threats) Present the comparison in 3 tables one for the comparison , second for the rating numerical rating (X/5) and a star rating (★ out of ★★★★★) for each feature  and  third for the SWOT analysis. Give heading to each table . After every table give two divider.
Instructions:
1. When asked for competitors of the given product, make sure that you provide only the name of the products and URLs of the products below the corresponding name.
2. The generated product URLs must be strictly from the automobile industry.
3. Title for Table 1: Feature Comparison
4. Title for Table 2: Rating Comparison
5. Make sure that the Rating Comparison table has both the numerical(X/5) and star rating(★ out of ★★★★★)
6. The products should be the column names in all the tables.
7. The font of the Table Title must be bold and the font size must be 40% bigger as compared to the rest of the text.
8. Add appropriate space between each section in the table.
9. Name the References as Competitors
```
![Configuration](assets/config_CA_2.png)  


> **Note:** The Google Search Tool is added by default to the Agent. However, if you accidentally click the delete icon, follow the Tool steps below. Otherwise, you can skip this.

#### Tools  

1. Click on the Add Tool.
![Add Tool](assets/add_tool.png)

2. Select **Google Search** as the tool to gather data.  
![Tool](assets/tool_link_search_agent.png)  

#### Saving and Deploying
Once the agent is created.

1. Click on the **Save As** button to save your Agent
2. click on the **Deploy** button to deploy the agent.
![Comparison Agent 1](assets/config_CA_3.png) 
3. After clicking on the save as button select Agent (marked as 1) and Click Save ((marked as 2))
![Comparison Agent 2](assets/config_CA_4.png)
4. Once you click on deploy, you need to create a user api key.  Click on "Create".
![Comparison Agent 3](assets/image44.0.1.png)
5. You'll be directed to another webpage. Click on "Create a key".
![Comparison Agent 4](assets/image44.0.2.png)
6. Once a key is created, navigate back to deployment page. Click on "Reload".
![Comparison Agent 4](assets/image44.1.png)
7. After clicking the deployment button make sure your Targeted deployment space has been selected and completed if not please select it.(marked as 1), click Deploy to deploy the agent (marked as 2)
![Comparison Agent 5](assets/config_CA_5.png)

> **YOU DID IT! you just created and deployed your first AI Agent.**
> Now let's build more agents and integrate them together.

## Integrating watsonx.ai's agent as an External Agent in watsonx Orchestrate

To deploy your agent on Orchestrate, follow the steps below: 

1. Go to the homepage of watsonx.ai Agent Lab.
![Home page](assets/agent_lab_homepage.png)

2. Click on the hamberger menu and select **Deployments**.  
![Deployments](assets/hamberger_agent_lab.png)

3. Click on the **Spaces** tab and select the space where you deployed the agent.  
![Spaces](assets/ca_dep.png)

4. Click on the **Assets** tab and select the agent.  
![Asset tab](assets/ca_dep2.png)

5. Then you will go the the main deployment page select your agent from the list.
![Deployment agent](assets/ca_dep3.png)

6. Then copy the public endpoint stream one.
![Deployment agent](assets/ca_url.png)

Then let's go to Orchestrate and create other agent and import this agent in that.

## Orchestrate Agent

In Orchestrate, we will create our main agent, as outlined below:

### Product Agent

1. Go to the Orchestrate home page, click on the hamburger menu (☰), select Build, and then choose Agent Builder.
![Agent Builder](assets/agent_build_wxo.png)

2. Click on the Create Agent button.
![Create Agent](assets/create_wxo.png)

3. Select Create from scratch (as shown in image 1 below), enter your agent’s name (as shown in image 2), provide a description (as shown in image 3), and then click the Create button (as shown in image 4).

   For Product Agent use the below description
        
   ```
   This agent is designed to search for a specified product and retrieve its details and features using Retrieval-Augmented Generation (RAG) on the product catalog. It presents the information in a clear and structured format, ensuring systematic organization of key product data, making it easy to understand and use.
   ```
   ![Create from scratch](assets/product_scratch.png)

4. After the agent is created, navigate to the Agent Configuration page.

   **Description:**
   ```
   Your knowledge base is the document that contains all the product-related information. All queries related to the product will be addressed using this document as the primary source.
   ```
   ![Knowledge](assets/product_knowledge.png)

5. Scroll down to the Knowledge section, then in the Document section, click on the Upload file button and upload [the product catalog](./assets/ABC_Motor_Product_Catalog.pdf).
![Upload file](assets/upload_file.png)

6. Scroll down to the Toolset section, then in the Agents section click on the Add Agent button.
![Add Agent](assets/add_agent_pa.png)

7. From the pop-up menu, select the Import.
![Add from local instance](assets/import_ca.png)

> **Note:** : We are now adding the Comparison Agent (an external agent) to the Product Agent, enabling it to delegate tasks to them.

8. On the next page, ensure that External Agent is selected (as shown in image 1 below). If it’s not already selected, please choose it, then click the Next button (as shown in image 2).
![Select External Agent](assets/external_agent_select.png)

9. On the next page, enter the following information:
      1. Provide: From the drop down select watsonx.ai.
      2. API key: Enter the watsonx.ai API key.
      3. Service instance URL: Enter the public endpoint URL of the agent that we copied in step 6.
      4. Display name: Enter the name of the agent.
      5. Description: Enter the below description.
      6. Click on the Import Agent button.

**Description:**
   ```
   This agent is designed to search for competitive URLs of input product and compare the given compare the given data with additional information gathered from Google search results. Its task is to carefully analyze the input data, extract key insights, and identify both differences and similarities. The findings should be presented in a well-structured table format, making it easy to understand and compare the information at a glance.

   ```
   ![External Agent](assets/external_agent_setup.png)

10. Once the delegated agents are added, they will appear as shown in the image below.
![Delegation Agent](assets/agent_appear_delegation.png)

11. Scroll down to the Behavior section, add the description shown in image as 1, and then click the Deploy button as shown in image as 2.

      For Product Agent use the below description in Behavior Section.

      ```
      This agent is responsible for handling product-related queries using Retrieval-Augmented Generation (RAG) on the product catalog.
      For general product queries, it retrieves structured information directly from the knowledge base.
      For queries involving URLs or web references or comparison, it delegates the task to the Comparison Agent.
      ```
      ![Behavior](assets/Product_agent_deploy.png)

> **Note:** : The Product Agent is now ready to handle product-related queries, delegating tasks to the Link Search Agent and Comparison Agent as needed.

## Experience Agents in Action
Follow the steps above, then try interacting with the use case using these sample queries:

1. Product Agent

   Ask the following questions to get responses from the Product Agent:
   ```
   Q1: What are the products of ABC Motors.
   ```
   ```
   Q2: Give me the info of Zenith X3.
   ```
   ![Product Agent Response](assets/chat_1.png)  

3. Comparison Agent

   To compare the retrieved data, ask:
   ```
   Give me URLs of the competitors of the above product and show me the comparison as well.
   ```
   ![Comparison Agent Response](assets/chat_2.png)  
   ![Comparison Agent Response 2](assets/chat_3.png)

Now, explore and experience the power of Skills & Agents in action! 🚀 
