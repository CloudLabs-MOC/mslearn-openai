# Lab 01: Get started with Azure OpenAI Service

### Estimated Duration: 40 minutes

## Lab Scenario
Azure OpenAI Service brings the generative AI models developed by OpenAI to the Azure platform, enabling you to develop powerful AI solutions that benefit from the security, scalability, and integration of services provided by the Azure cloud platform. In this exercise, you'll learn how to get started with Azure OpenAI by provisioning the service as an Azure resource and using Azure OpenAI Studio to deploy and explore OpenAI models.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Explore a model in the Completions playground
- Task 4: Use the Chat playground
- Task 5: Explore prompts and parameters 
- Task 6: Explore code-generation

### Task 1: Provision an Azure OpenAI resource

Before you can use Azure OpenAI models, you must provision an Azure OpenAI resource in your Azure subscription.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/openai8.png)

2. On **Azure AI Services | Azure OpenAI** blade, click on **+ Create**.

   ![](../media/openai_create1.png)

3. Create an **Azure OpenAI** resource with the following settings:
   
    - **Subscription**: Default - Pre-assigned subscription.
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Region**: Select <inject key="Region" enableCopy="false" />
    - **Name**: OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Pricing tier**: Standard S0
  
   ![](../media/openai-lab01_01.png "Create Azure OpenAI resource")

4. Click on **Next** thrice and click on **Create**.

5. Wait for deployment to complete. Then go to the deployed Azure OpenAI resource in the Azure portal.

#### Validation

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

   <validation step="1fa0e87b-eb46-463d-b63b-edf6e2282e16" />

### Task 2: Deploy a model

Azure OpenAI provides a web-based portal named **Azure OpenAI Studio**, that you can use to deploy, manage, and explore models. You'll start your exploration of Azure OpenAI by using Azure OpenAI Studio to deploy a model.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/openai8.png)

2. On **Azure AI Services | Azure OpenAI** blade, select **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/OpenAI_select.png)

3. In the Azure OpenAI resource pane, click on **Go to Azure OpenAI Studio** it will navigate to **Azure AI Studio**.

   ![](../media/openai_studio.png)

4. After navigating to Azure AI Studio, click on **Explore the new experience** pop-up on the top.

   ![](../media/explore_new-exp.jpg)

5. Click on **Deployments (1)** from the left navigation pane, click on **+ Deploy model** , select **Deploy base Model (2)**.  

   ![](../media/deploy-2.jpg)

6. In the **Select a model** window, select **gpt-35-turbo (1)** and click on **Confirm (2)**.

   ![](../media/mew5.png)

7. Within the **Deploy model** pop-up interface, enter the following details:
    
    - **Deployment name**: my-gpt-model (1) 
    - **Model version**: 0613 (2)
    - **Deployment type**: Standard (3)
    - **Tokens per Minute Rate Limit (thousands)**: 10K (4)
    - **Enable dynamic quota**: Enabled (5)
    - Click on **Deploy** (6)
  
      ![](../media/new3.png)

8. This will deploy a model which you will be playing around with as you proceed.

   > **Note**: You can ignore any error related to the assignment of roles to view the quota limits.

   > **Note**: Azure OpenAI includes multiple models, each optimized for a different balance of capabilities and performance. In this exercise, you'll use the **GPT-35-Turbo** model, which is a good general model for summarizing and generating natural language and code. For more information about the available models in Azure OpenAI, see [Models](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) in the Azure OpenAI documentation.

#### Validation

<validation step="3b4a472e-f956-45d8-b828-3e2cc01c2e88" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.


### Task 3: Explore a model in the Completions playground

*Playgrounds* are useful interfaces in Azure OpenAI Studio that you can use to experiment with your deployed models without needing to develop your own client application.

1. In Azure OpenAI Studio, in the left pane under **Playground**, select **Completions**.

2. In the **Completions** page, ensure your **my-gpt-model** deployment is selected and then in the **Examples** list, select **Generate a quiz**.

    The summarised text sample consists of a *prompt* that provides some text to tell the model what kind of response is required and includes some contextual information.

3. At the bottom of the page, note the number of *tokens* detected in the text. Tokens are the basic units of a prompt - essentially words or word parts in the text.

4. Use the **Generate** button to submit the prompt to the model and retrieve a response.

    The response consists of a quiz based on the example in the prompt.

    >**Note**: You can use the **Regenerate** button to resubmit the prompt(new changes have been made), and note that the response may vary from the original one. A generative AI model can produce a new language each time it's called.

5. Use the **View Code** button to view the code that a client application would use to submit the prompt. You can select your preferred programming language. The prompt contains the text you submitted to the model. The request is submitted to the *Completions* API for your Azure OpenAI service.

### Task 4: Use the Chat playground

The *Chat* playground provides a chatbot interface for GPT 3.5 and higher models. It uses the *ChatCompletions* API rather than the older *Completions* API.

1. In the **Playground** section, select the **Chat** page, and ensure that the **my-gpt-model** model is selected in the configuration pane.

2. In the **Setup** section, in the **System message** box, replace the current text with the following statement: `The system is an AI teacher that helps people learn about AI`.

3. Below the **System message** box, click on **+ Add**, and enter the following message and response in the designated boxes:

    - **User**: `What are different types of artificial intelligence?`
    
    - **Assistant**: `There are three main types of artificial intelligence: Narrow or Weak AI (such as virtual assistants like Siri or Alexa, image recognition software, and spam filters), General or Strong AI (AI designed to be as intelligent as a human being. This type of AI does not currently exist and is purely theoretical), and Artificial Superintelligence (AI that is more intelligent than any human being and can perform tasks that are beyond human comprehension. This type of AI is also purely theoretical and has not yet been developed).`

    > **Note**: Few-shot examples are used to provide the model with examples of the types of responses that are expected. The model will attempt to reflect the tone and style of the examples in its own responses.
  
4. Click on **Apply changes** and then click on **Continue** in the **Update system message** pop-up tab to start a new session and set the behavioural context of the chat system.

5. In the query box at the bottom of the page, enter the text `What is artificial intelligence?`

6. Use the **Send** button to submit the message and view the response.

    > **Note**: You may receive a response that the API deployment is not yet ready. If so, wait for a few minutes and try again.

7. Review the response and then submit the following message to continue the conversation: `How is it related to machine learning?`

8. Review the response, noting that context from the previous interaction is retained (so the model understands that "it" refers to artificial intelligence).

9. Use the **View Code** button to view the code for the interaction. The prompt consists of the *system* message, the few-shot examples of *user* and *assistant* messages, and the sequence of *user* and *assistant* messages in the chat session so far.

### Task 5: Explore prompts and parameters

You can use the prompt and parameters to maximize the likelihood of generating the response you need.

1. In the **Configuration** pane select **Parameter** , set the following parameter values:
    - **Temperature**: 0
    - **Max response (Max number of tokens)**: 500

2. Submit the following message in the chat session 

    ```
    Write three multiple choice questions based on the following text.

    Most computer vision solutions are based on machine learning models that can be applied to visual input from cameras, videos, or images.*

    - Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on.*

    - Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use object detection to identify the location of different classes of vehicle.*

    - Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution might overlay traffic images with "mask" layers to highlight different vehicles using specific colors.
    ```

3. Review the results, which should consist of multiple-choice questions that a teacher could use to test students on the computer vision topics in the prompt. The total response should be smaller than the maximum length you specified as a parameter.

    Observe the following about the prompt and parameters you used:

    - The prompt specifically states that the desired output should be three multiple choice questions.
    
    - The parameters include *Temperature*, which controls the degree to which response generation includes an element of randomness. The value of **0** used in your submission minimizes randomness, resulting in stable, predictable responses.

### Task 6: Explore code-generation

In addition to generating natural language responses, you can use GPT models to generate code.

1. In the **Setup** pane, select the **Empty Example** template and then click on **Continue** in the **Update system message** pop up tab to reset the system message.

2. Enter the system message: `You are a Python developer.` and click on **Apply changes** and then click on **Continue** in the **Update system message** pop-up tab.

3. In the **Chat session** pane, select **Clear chat** and then click on **Clear** in the clear chat tab to clear the chat history and start a new session.

4. Submit the following user message:

    ```
    Write a Python function named Multiply that multiplies two numeric parameters.
    ```

5. Review the response, which should include sample Python code that meets the requirement in the prompt.

## Summary

In this lab, you have accomplished the following:
-   Provision an Azure OpenAI resource
-   Deploy an Azure OpenAI model within the Azure OpenAI studio
-   Use the chat playground to utilize the functionalities of prompts, parameters and code generation

### You have successfully completed the lab.
