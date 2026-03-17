# Lab 02: Explore AI Agent development

### Estimated Duration: 30 Minutes

## Overview

In this lab, you will create and configure an AI agent using the Microsoft Foundry portal to assist employees with expense claims. You will build a project, define agent instructions, and ground responses using an expense policy document. Finally, you will test the agent in the playground by asking policy questions and generating an expense claim file that you can download and review.

> **Note:** Some of the technologies used in this exercise are in preview or in active development. You may experience some unexpected behavior, warnings, or errors.

## Lab Objectives

In this lab, you'll perform the following tasks:

- **Task 1:** Create a Foundry project and agent

- **Task 2:** Configure your agent

- **Task 3:** Test your agent

## Task 1: Create a Foundry project and agent

In this task, you will sign in to the Microsoft Foundry portal, create a new Foundry project, and create an AI agent in the playground. By completing this task, you will have a ready-to-use project and agent with a deployed model available for configuration.

1. Open a new tab in the browser, right-click on the following link [Foundry portal](https://ai.azure.com), then **Copy link** and paste it in a browser tab to log in to **Microsoft Foundry portal**.

1. Click on **Sign in**.
 
    ![](../media/lab1-s2.png)

1. If prompted, provide the credentials below:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
    
     ![](../media/lab1-s3.png)

   - **Password:** <inject key="AzureAdUserPassword"></inject>
    
     ![](../media/lab1-s4.png)

1. When the **Stay signed in?** window appears, select **No**.

    ![](../media/lab1-s5.png)

    >**Note:** Close any tips or quick start panes that are opened the first time you sign in, and if necessary use the **Foundry** logo at the top left to navigate to the home page, which looks similar to the following image (close the **Help** pane if it's open):

1. At the top of the **Microsoft Foundry** portal, enable the **New Foundry toggle (1)** to switch to the latest Foundry user interface.

1. From the **Select a project to continue** dialog, click the drop-down under **Select or search for a project**, and then select **Create a new project (2)**.

     ![](../media/lab1-s6.png)

1. In the **Create a project** window, enter **Myprojects-<inject key="DeploymentID"></inject> (1)** as the project name. Open the **Advanced options (2)** drop-down, fill in the following details, and then click **Create (7)**:

    * **Subscription:** **Choose Default Subscription (3)**
    * **Resource group:** **AI-3026-RG (4)**
    * **Microsoft Foundry resource:** **Keep as Default (5)**
    * **Region:** **<inject key="Region"></inject> (6)**

      ![](../media/lab1-02-1.png)

      >**Note:** Some Azure AI resources are constrained by regional model quotas. In the event of a quota limit being exceeded later in the exercise, there's a possibility you may need to create another resource in a different region.

1. Wait for your project created. It may take a few minutes.

1. On the **Microsoft Foundry** home page, click **Start building (1)**, and then select **Browse models (2)** from the drop-down menu.

     ![](../media/lab2-s2.png)

1. On the **Models** page, search for **gpt-4.1 (1)** in the search bar, and then select the **gpt-4.1 (2)** model from the search results.

     ![](../media/lab2-s3.png)

1. On the **gpt-4.1** model page, select **Deploy (1)**, and then choose **Custom settings (2)**.

    ![](../media/lab1-02-2.png)

1. In the **Deploy gpt-4.1** pane, verify **Standard (1)** is selected under **Deployment type**, and then click **Deploy (2)**.

    ![](../media/lab1-02-3.png)

1. In the left navigation, select **Agents (1)**, and then choose **Create agent (2)** to create a new agent.

    ![](../media/lab1-02-01.png)

1. In the **Create an agent** pane, enter **expense-agent (1)** in the **Agent name** field, and then select **Create (2)**.

    ![](../media/lab1-02-02.png)

1. In the navigation bar on the left, select **Microsoft Foundry** to return to the Foundry home page.

     ![](../media/lab1-02-5.png)

1. Copy the **Project endpoint** value to a notepad, as you'll use them to connect to your project in a client application.

    ![](../media/lab2-s6.png)

    > **Note:** Copy and save the **Project endpoint** in a notepad, as it will be required in upcoming labs.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
>
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help.
 
<validation step="87f3da8f-5149-49a6-9189-901881587c0c" />

## Task 2: Configure your agent

In this task, you will configure your agent by adding instructions, uploading an expense policy document for grounding, and enabling the required tools.

1. Open another browser tab, and download [Expenses_policy.docx](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/01-agent-fundamentals/Expenses_Policy.docx) from `https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-agents/main/Labfiles/01-agent-fundamentals/Expenses_Policy.docx` and save it locally. This document contains details of the expenses policy for the fictional Contoso corporation.

1. Return to the browser tab where you have the **Microsoft Foundry** portal open.

1. In the top navigation, select **Build (1)**, and then choose **expense-agent (2)** from the Agents list.

    ![](../media/lab1-02-03.png)

1. In **Instructions (1)**, enter the provided prompt text

    ```prompt
   You are an AI assistant for corporate expenses.
   You answer questions about expenses based on the expenses policy data.
   If a user wants to submit an expense claim, you get their email address, a description of the claim, and the amount to be claimed and write the claim details to a text file that the user can download.
    ```

1. Below the **Instructions**, expand the **Tools** section. Select **Upload files (2)**

    ![](../media/lab1-s10.png)

1. Keep the default values for the **Index option** and **Vector index name**.

1. Select the **browse for files** option to upload the **Expenses_policy.docx** local file that you downloaded previously.

      ![](../media/lab1-s11.png)

1. In the **Open dialog** box, select **Downloads (1)**, choose the **expenses_policy file (2)**, and then select **Open (3)** to upload the file.

    ![](../media/lab1-s12.png)

1. When your file is successfully uploaded, select **Attach**.

    ![](../media/lab1-s13.png)

1. In the **Tools** section, verify that a new **File search (1)** is listed and shown as containing 1 file.

1. In the **Tools** section, select **Add (2)**.

    ![](../media/lab1-02-6.png)

1. In the **Select a tool** dialog box, select **Code interpreter (1)** and then select **Add tool (2)** (you do not need to upload any files for the code interpreter).

    ![](../media/lab1-s15.png)

    - Your agent will use the document you uploaded as its knowledge source to *ground* its responses (in other words, it will answer questions based on the contents of this document). It will use the code interpreter tool as required to perform actions by generating and running its own Python code.

1. On the **expense-agent** page, select **Save**.

    ![](../media/lab1-02-7.png)

## Task 3: Test your agent

In this task, you will test your configured agent in the playground by asking policy-related questions and submitting an expense claim to verify its responses and actions.

1. In the **Playground** chat box, enter `What's the maximum I can claim for meals?` **(1)**, and then select **Send (2)**.

    ![](../media/lab1-s17.png)

1. Review the agent’s response and confirm it is based on the uploaded **Expenses_Policy.docx** knowledge source.

    ![](../media/lab1-s17.1.png)

    > **Note:** If the agent fails to respond because the rate limit is exceeded. Wait a few seconds and try again. If there is insufficient quota available in your subscription, the model may not be able to respond. If the problem persists, try to increase the quota for your model on the **Models** page.

1. Try the following follow-up prompt: `I'd like to submit a claim for a meal.` and review the response. The agent should ask you for the required information to submit a claim.

    ![](../media/lab1-s18.png)

1. Provide the agent with an email address; for example, `fred@contoso.com`. The agent should acknowledge the response and request the remaining information required for the expense claim (description and amount)

    ![](../media/lab1-s19.png)

1. Submit a prompt that describes the claim and the amount; for example, `Breakfast cost me $20`.

1. The agent should use the code interpreter to prepare the expense claim text file, and provide a link so you can download it.

    ![](../media/lab1-s20.png)

1. Download and open the text document to see the expense claim details.

## Optional: Explore the code

After experimenting with your agent in the playground, you may want to integrate it into your own client application. The **Code** tab provides sample code that shows how to interact with your agent programmatically.

1. In the agent playground, select the **Code** tab to view the sample code.

    ![](../media/lab1-s21.png)

1. Review the Python code. This code demonstrates how to:
    - Connect to your agent using the Azure AI Projects SDK
    - Send messages to the agent
    - Retrieve and process responses
    
1. Select **.env variables** to view the environment variables you need to run this code.

    ![](../media/lab1-s22.png)

1. You can use this code as a starting point for building your own client application that interacts with the agent you created.

1. Optionally, select **Open in VS Code for the Web** to launch a preconfigured workspace with the sample code ready to run.

    > **Note:** It may take a few minutes for the workspace to be prepared. Follow the instructions provided in the workspace to successfully run the code.

## Summary

In this lab, you created a new project in the Microsoft Foundry portal and built an AI agent to assist with expense claims. You configured the agent with system instructions and added an expense policy document as grounding data. You also enabled the code interpreter tool so the agent could perform actions. Finally, you tested the agent in the playground by asking policy questions and generating an expense claim file to download and review.

### You have successfully completed the lab. Click on **Next >>** to proceed with the next Lab.

   ![](../media/ai-3026next1.png)