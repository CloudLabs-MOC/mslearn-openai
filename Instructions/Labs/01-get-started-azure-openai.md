# Lab 01: Get started with Azure OpenAI Service

## Lab scenario
Azure OpenAI Service brings the generative AI models developed by OpenAI to the Azure platform, enabling you to develop powerful AI solutions that benefit from the security, scalability, and integration of services provided by the Azure cloud platform. In this exercise, you'll learn how to get started with Azure OpenAI by provisioning the service as an Azure resource and using Azure AI Foundry portal to deploy and explore OpenAI models.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Explore a model in the Completions playground
- Task 4: Use the Chat playground
- Task 5: Explore prompts and parameters 
- Task 6: Explore code-generation

## Estimated time: 60 minutes

### Task 1: Provision an Azure OpenAI resource

In this task , you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/tel-11.png)

1. On **Azure AI Services | Azure OpenAI** blade, select **Azure OpenAI (1)** from left pane and click on **Create (2)**.

   ![](../media/tel-10.png)

1. Create an **Azure OpenAI** resource with the following settings then click on **Next** thrice and then click on **Create**.
    - **Subscription**: Default - Pre-assigned subscription. **(1)**
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject> **(2)**
    - **Region**: Select **Sweden Central (3)**
    - **Name**: OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> **(4)**
    - **Pricing tier**: Standard S0 **(5)**
    - Click on **Next**.
      
         ![](../media/open-ai9.png "Create Azure OpenAI resource")

    - On the **Network tab** select the **All networks, including the internet, can access this resource (1)** and click on **Next (2)**.

         ![](../media/ai01.png)
      
    - On the **Tags tab** click on **Next**.
      
    - On the **Review + Submit tab**, after validation passes, click on **Create**.

         ![](../media/ai04.png)

1. Wait for deployment to complete. Then go to the deployed Azure OpenAI resource in the Azure portal.

   <validation step="917cb723-2d65-4411-90f9-0150a7636494" />

   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
   > - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. In the **Azure portal**, search for **Azure OpenAI** and select **Azure OpenAI**.

      ![](../media/tel-11.png)

2. On the **Azure AI Services** page, ensure that **Azure OpenAI (1)** is selected from the left blade. Then, select **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> (2)**.

      ![](../media/update07.png)

3. In **Overview (1)** section, click on **Go to Azure AI Foundry portal (2)**, it will navigate to **Azure AI Foundry portal**.

      ![](../media/update08.png)

4. On the **Azure AI Foundry portal** page, select **Deployments (1)** under **Shared Resources** from the left pane. Then, click **+ Deploy Model** and choose **Deploy Base Model (2)**.

      ![](../media/ui1.png)

5. Search for **gpt-4o-mini**, click on **Confirm**

   ![](../media/gpt-4-mini.png)
   
6. Within the **Deploy model** pop-up interface, enter the following details:
      - **Deployment name**: my-gpt-model (1)
      - **Deployment type**: Standard(2)
      - Click on **Customize**
      - **Model version**:2024-07-18(default) (3)
      - **Tokens per Minute Rate Limit (thousands)**: 10K (4)
      - **Content Filter**: DefaultV2 (5)
      - **Enable dynamic quota**: Enabled (6)
      - Click on **Deploy** (7)
  
           ![](../media/gpt-4omini.png)

           >**Note** : gpt-4o-mini is supported only for chat completions and it is not supported for completions API.

7. Click the back arrow on the newly created model, then select **Deployments (1)** under **Shared Resources** in the left pane. After that, click **+ Deploy Model** and choose **Deploy Base Model (2)**.

      ![](../media/ui1.png)

9. Search for **gpt-35-turbo-instruct**, click on **Confirm**.

   ![](../media/ui4b.png)
   
9. Within the **Deploy model** pop-up interface, enter the following details:
      - **Deployment name**: gpt-35-turbo-instruct (1)
      - **Deployment type**: Standard(2)
      - Click on **Customize**.
      - **Model version**: 0914 (Default) (3)
      - **Tokens per Minute Rate Limit (thousands)**: 20K (4)
      - **Enable dynamic quota**: Enabled (5)
      - Click on **Deploy** (6)
  
      ![](../media/image1b.png)

10. These will deploy models that you can experiment with for both chat and completion tasks as you go along.

      > **Note**: You can ignore any error related to assignment of roles to view the quota limits. 

   <validation step="0afa9e73-8b9e-4edf-b61b-fa953a5d5b23" />
   
   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 3: Explore a model in the Completions playground

In this task ,You'll Explore a model in the Completions playground involves interacting with the AI model to test and refine its responses using real-time input and output examples.

1. In **Azure AI Foundry portal**, in the left pane under **Playground**, select **Completions**.

1. In the **Completions (1)** page, ensure your **gpt-35-turbo-instruct (2)** deployment is selected , Type **Generate a quiz (3)** in the prompt and then click on **Generate (4)**

      ![](../media/completion01.png)

      >**Note:** The summarize text sample consists of a *prompt* that provides some text to tell the model what kind of response is required and include some contextual information.

1. At the bottom of the page, note the number of *tokens* detected in the text. Tokens are the basic units of a prompt - essentially words or word-parts in the text.

1. Use the **Generate** button to submit the prompt to the model and retrieve a response (you may need to scroll down). The response consists of a quiz based on the example in the prompt.

      ![](../media/completion03.png)

      >**Note**: You can use the **Regenerate** button to resubmit the prompt(new changes have been made), and note that the response may vary from the original one. A generative AI model can produce new language each time it's called.

1. Use the **View Code** button to view the code that a client application would use to submit the prompt. 

      ![](../media/completion02.png)

1. You can select your preferred programming language **(1)** then naviage to the **Key authentication (2)**.The prompt contains the text you submitted to the model. The request is submitted to the *Completions* API for your Azure OpenAI service.      

      ![](../media/open-ai1.png)
    
7. Close the **Sample Code**.

### Task 4: Use the Chat playground

In this task, you'll use the Chat playground to interact with and test the AI model's conversational abilities through a simulated chat interface.

1. In the **Playground** section, select the **Chat (1)** page, and ensure that the **my-gpt-model (2)** model is selected in the Deployment pane.

      ![](../media/chat001.png)

1. In the **Setup** section, in the **Give the model instructions and context** box, replace the current text with the following statement: `The system is an AI teacher that helps people learn about AI`.

1. Below the **+ Add section** box, click on **Examples**. enter the following message and response in the designated boxes:

      ![](../media/chat002.png)

1.  Enter the following message and response in the designated boxes:

       - **User**: `What are different types of artificial intelligence?`
    
       - **Assistant**: `There are three main types of artificial intelligence: Narrow or Weak AI (such as virtual assistants like Siri or Alexa, image recognition software, and spam filters), General or Strong AI (AI designed to be as intelligent as a human being. This type of AI does not currently exist and is purely theoretical), and Artificial Superintelligence (AI that is more intelligent than any human being and can perform tasks that are beyond human comprehension. This type of AI is also purely theoretical and has not yet been developed).`

            ![](../media/exples-ai.jpg)
   
            > **Note**: Few-shot examples are used to provide the model with examples of the types of responses that are expected. The model will attempt to reflect the tone and style of the examples in its own responses.

1. Save the changes by clicking on **Apply changes (1)** and subsequently click on **Continue (2)** to start a new session and set the behavioral context of the chat system.

      ![](../media/open-ai3.png)   

1. In the query box at the bottom of the page, enter the text `What is artificial intelligence?`.  **(1)** Use the **Send (2)** button to submit the message and view the response.

      ![](../media/chat003.png)
   
      > **Note**: You may receive a response that the API deployment is not yet ready. If so, wait for a few minutes and try again.

1. Review the response and then submit the following message to continue the conversation: `How is it related to machine learning?`

1. Review the response, noting that context from the previous interaction is retained (so the model understands that "it" refers to artificial intelligence).

1. Use the **View Code** button to view the code for the interaction. The prompt consists of the *system* message, the few-shot examples of *user* and *assistant* messages, and the sequence of *user* and *assistant* messages in the chat session so far.

      ![](../media/chat004.png)

      ![](../media/open-ai4.png)       

### Task 5: Explore prompts and parameters

In this task, you'll explore prompts and parameters by experimenting with different inputs and settings to fine-tune the AI model's responses and behavior.

1. On the **Setup** page select **Parameters (1)** , set the following parameter values:
    
    - **Temperature**: 0 **(2)**
    
    - **Max response**: 500 **(3)**

         ![](../media/chat005.png)
         ![](../media/open-ai5-2.png)
      
2. Submit the following message in chat session

      ```
     Write three multiple choice questions based on the following text.

      Most computer vision solutions are based on machine learning models that can be applied to visual input from cameras, videos, or images.*

      - Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to    
        classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on.*

      - Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use 
        object detection to identify the location of different classes of vehicle.*

      - Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution 
        might overlay traffic images with "mask" layers to highlight different vehicles using specific colors.
      ```

3. Review the results, which should consist of multiple-choice questions that a teacher could use to test students on the computer vision topics in the prompt. The total response should be smaller than the maximum length you specified as a parameter.

      ![](../media/last-3.jpg)
   
4. Observe the following about the prompt and parameters you used:
       - The prompt specifically states that the desired output should be three multiple choice questions.
       - The parameters include *Temperature*, which controls the degree to which response generation includes an element of randomness. The value of **0** used in your submission minimizes randomness, resulting in stable, predictable responses.

>**Note:** Before proceeding to Task 6, make sure to delete any examples you added under the Example section.

   ![](../media/chat007.png)

### Task 6: Explore code-generation

In this task, you'll explore code-generation by testing the AI model’s ability to generate and suggest code snippets based on various programming prompts and requirements.

1. In the **Setup** section, in the **Give the model instructions and context** box, enter the text: `You are a Python developer.` **(1)** then save the changes by clicking on **Apply Changes (2)** when prompted click on **Continue (3)**.

      ![](../media/chat006.png)

1. In the **Chat session** pane, select **Clear chat** to clear the chat history and start a new session.

1. Submit the following user message:

      ```
     Write a Python function named Multiply that multiplies two numeric parameters.
      ```

1. Review the response, which should include sample Python code that meets the requirement in the prompt.

      ![](../media/open-ai8.png)

## Summary

In this lab, you have accomplished the following:
-   Provision an Azure OpenAI resource
-   Deploy an Azure OpenAI model within the Azure AI Foundry portal
-   Use the chat playground to utilize the functionalities of prompts, parameters and code-generation

##   You have successfully completed the lab.
