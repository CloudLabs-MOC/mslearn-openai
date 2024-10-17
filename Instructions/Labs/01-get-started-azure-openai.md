# Lab 01: Get started with Azure OpenAI Service

## Lab scenario
Azure OpenAI Service brings the generative AI models developed by OpenAI to the Azure platform, enabling you to develop powerful AI solutions that benefit from the security, scalability, and integration of services provided by the Azure cloud platform. In this exercise, you'll learn how to get started with Azure OpenAI by provisioning the service as an Azure resource and using Azure OpenAI Studio to deploy and explore OpenAI models.

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

1. On **Azure AI Services | Azure OpenAI** blade, click on **Create**.

   ![](../media/tel-10.png)

1. Create an **Azure OpenAI** resource with the following settings then click on **Next** thrice and then click on **Create**.
    - **Subscription**: Default - Pre-assigned subscription. **(1)**
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject> **(2)**
    - **Region**: Select **France Central (3)**
    - **Name**: OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> **(4)**
    - **Pricing tier**: Standard S0 **(5)**
  
         ![](../media/open-ai9.png "Create Azure OpenAI resource")

1. Wait for deployment to complete. Then go to the deployed Azure OpenAI resource in the Azure portal.

   <validation step="917cb723-2d65-4411-90f9-0150a7636494" />

   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
   > - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

      ![](../media/tel-11.png)

1. On **Azure AI Services | Azure OpenAI** blade, select **OpenAI-Lab01-<inject key="Deployment-id" enableCopy="false"></inject>**

      ![](../media/tel-1.png)

1. In the Azure OpenAI resource pane, click on **Go to Azure OpenAI Studio** it will navaigate to **Azure AI Studio**.

      ![](../media/new01.png)
   
1. In the **Deployments (1)** page, click on **+ Deploy model** , Choose **Deploy base Model (2)**.

      ![](../media/ui1.png "Create a new deployment")

      > **Note**: Click on the **Expand** button, if you dont see the left side navigation pane.

      ![](../media/code2.png "Keys and Endpoints")           

1. Search for **GPT-35-TURBO**, click on **Confirm**

      ![](../media/pg-09.jpg)
   
1. Within the **Deploy model** pop-up interface, enter the following details:
      - **Deployment name**: my-gpt-model (1)
      - **Model version**: 0301(Default)(2)
      - **Deployment type**: Standard(3)
      - **Tokens per Minute Rate Limit (thousands)**: 10K (4)
      - **Enable dynamic quota**: Enabled (5)
      - Click on **Deploy** (6)
  
           ![](../media/i1.png)

           >**Note** : gpt-35-turbo-16k is supported only for chat completions and it is not supported for completions API.
           
           > **Note**: If you see the interface like the below screenshot, Click on **Customize** and provide the details.

           ![](../media/code10.png "Keys and Endpoints")           

1. This will deploy a model which you will be playing around with as you proceed.

      > **Note**: You can ignore any error related to assignment of roles to view the quota limits. 
   
      > **Note**: Azure OpenAI includes multiple models, each optimized for a different balance of capabilities and performance. In this exercise, you'll use the **GPT-35-Turbo** model, which is a good general model for summarizing and generating natural language and code. For more information about the available models in Azure OpenAI, see [Models](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) in the Azure OpenAI documentation.

   <validation step="0afa9e73-8b9e-4edf-b61b-fa953a5d5b23" />
   
   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 3: Explore a model in the Completions playground

In this task ,You'll Explore a model in the Completions playground involves interacting with the AI model to test and refine its responses using real-time input and output examples.

1. In Azure OpenAI Studio, in the left pane under **Playground**, select **Completions**.

1. In the **Completions (1)** page, ensure your **my-gpt-model (2)** deployment is selected , Type **Generate a quiz (3)** in the prompt and then click on **Generate (4)**

      ![](../media/generate_new.jpg)

      >**Note:** The summarize text sample consists of a *prompt* that provides some text to tell the model what kind of response is required and include some contextual information.

1. At the bottom of the page, note the number of *tokens* detected in the text. Tokens are the basic units of a prompt - essentially words or word-parts in the text.

1. Use the **Generate** button to submit the prompt to the model and retrieve a response (you may need to scroll down). The response consists of a quiz based on the example in the prompt.

      ![](../media/generated.jpg)

      >**Note**: You can use the **Regenerate** button to resubmit the prompt(new changes have been made), and note that the response may vary from the original one. A generative AI model can produce new language each time it's called.

1. Use the **View Code** button to view the code that a client application would use to submit the prompt. 

      ![](../media/view_code.jpg)

1. You can select your preferred programming language **(1)** then naviage to the **Key authentication (2)**.The prompt contains the text you submitted to the model. The request is submitted to the *Completions* API for your Azure OpenAI service.      

      ![](../media/open-ai1.png)
    
7. Close the **Sample Code**.

### Task 4: Use the Chat playground

In this task, you'll use the Chat playground to interact with and test the AI model's conversational abilities through a simulated chat interface.

1. In the **Playground** section, select the **Chat (1)** page, and ensure that the **my-gpt-model (2)** model is selected in the configuration pane.

      ![](../media/open-ai2.png)

1. In the **Setup** section, in the **System message** box, replace the current text with the following statement: `The system is an AI teacher that helps people learn about AI`.

1. Below the **+ Add section** box, click on **Examples**. enter the following message and response in the designated boxes:

      ![](../media/last-2.jpg)

1.  Enter the following message and response in the designated boxes:

       - **User**: `What are different types of artificial intelligence?`
    
       - **Assistant**: `There are three main types of artificial intelligence: Narrow or Weak AI (such as virtual assistants like Siri or Alexa, image recognition software, and spam filters), General or Strong AI (AI designed to be as intelligent as a human being. This type of AI does not currently exist and is purely theoretical), and Artificial Superintelligence (AI that is more intelligent than any human being and can 
perform tasks that are beyond human comprehension. This type of AI is also purely theoretical and has not yet been developed).`

            ![](../media/exples-ai.jpg)
   
            > **Note**: Few-shot examples are used to provide the model with examples of the types of responses that are expected. The model will attempt to reflect the tone and style of the examples in its own responses.

1. Save the changes by clicking on **Save (1)** and subsequently click on **Continue (2)** to start a new session and set the behavioral context of the chat system.

      ![](../media/open-ai3.png)   

1. In the query box at the bottom of the page, enter the text `What is artificial intelligence?`.  **(1)** Use the **Send (2)** button to submit the message and view the response.

      ![](../media/openai-12.png)
   
      > **Note**: You may receive a response that the API deployment is not yet ready. If so, wait for a few minutes and try again.

1. Review the response and then submit the following message to continue the conversation: `How is it related to machine learning?`

1. Review the response, noting that context from the previous interaction is retained (so the model understands that "it" refers to artificial intelligence).

1. Use the **View Code** button to view the code for the interaction. The prompt consists of the *system* message, the few-shot examples of *user* and *assistant* messages, and the sequence of *user* and *assistant* messages in the chat session so far.

      ![](../media/view_code.jpg)

      ![](../media/open-ai4.png)       

### Task 5: Explore prompts and parameters

In this task, you'll explore prompts and parameters by experimenting with different inputs and settings to fine-tune the AI model's responses and behavior.

1. On the **Setup** page select **Parameter (1)** , set the following parameter values:
    
    - **Temperature**: 0 **(2)**
    
    - **Max response**: 500 **(3)**

        ![](../media/open-ai5.png)
      
1. Submit the following message in chat session

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

1. Review the results, which should consist of multiple-choice questions that a teacher could use to test students on the computer vision topics in the prompt. The total response should be smaller than the maximum length you specified as a parameter.

      ![](../media/last-3.jpg)
   
1. Observe the following about the prompt and parameters you used:
       - The prompt specifically states that the desired output should be three multiple choice questions.
       - The parameters include *Temperature*, which controls the degree to which response generation includes an element of randomness. The value of **0** used in your submission minimizes randomness, resulting in stable, predictable responses.

### Task 6: Explore code-generation

In this task, you'll explore code-generation by testing the AI model’s ability to generate and suggest code snippets based on various programming prompts and requirements.

1. In the **Setup** pane, under the **System message**, enter the system message: `You are a Python developer.` **(1)** then save the changes by clicking on **Save (2)** when prompted click on **Continue (3)**.

      ![](../media/open-ai7.png)

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
-   Deploy an Azure OpenAI model within the Azure OpenAI studio
-   Use the chat playground to utilize the functionalities of prompts, parameters and code-generation

##   You have successfully completed the lab.
