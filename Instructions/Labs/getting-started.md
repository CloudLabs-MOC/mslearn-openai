# Generate Code and Images with Azure OpenAI Services

### Overall Estimated Duration: 4 Hours

## Overview

In this hands-on-lab, you will explore the capabilities of Azure OpenAI Service models in generating and enhancing code using natural language prompts. You will learn how these models can assist in coding by generating new code, fixing bugs in existing code, and providing detailed comments. Additionally, you will gain an understanding of how these models can explain and simplify complex code, making it easier to comprehend and improve. The lab will also introduce you to the DALL-E model, where you will practice generating original images by submitting natural language prompts, focusing on the creative potential of AI in visual content creation.

## Objective 

This exercise aims to improve your skills in generating and refining code with Azure OpenAI and creating and modifying images using the DALL-E model to achieve desired outcomes. By completing this lab, you will learn:

1. **Generate and improve code with Azure OpenAI Service**: The goal of this hands-on exercise is to demonstrate how to effectively generate and refine code using Azure OpenAI. You will improve your abilities to create and refine code with Azure OpenAI Service tools and approaches.

2. **Generate images with a DALL-E model**: The goal of this hands-on activity is to produce and alter images using the DALL-E model. To attain the intended visual results, you will develop and alter images using the DALL-E model.

## Prerequisites

1. **Development Skills**: Basic programming knowledge and experience with APIs and SDKs.
2. **AI Concepts**: Understanding prompt engineering, code development, and image generation using models such as DALL-E.
3. **Content Management**: Understanding data integration for RAG and content filtering techniques.
   
## Architecture

In this hands-on lab, you will follow an architecture flow that begins with exploring Azure OpenAI Service models, where you'll use natural language prompts to generate and enhance code. The flow progresses through stages of code generation, bug fixing, and detailed commenting, leveraging AI to simplify and explain complex code. The final stage introduces the DALL-E model, where you'll practice generating original images from natural language prompts, highlighting the creative potential of AI in visual content creation. This flow seamlessly integrates AI-driven coding and creative image generation, providing a comprehensive understanding of Azure OpenAI's capabilities.

## Architecture Diagram

   ![](../media/ARCH10.PNG)

## Explanation of Components

- **Azure OpenAI**: Integrates your data with massive language models, allowing for personalized and secure interactions.Allows for fine-tuning of AI models with your own datasets, resulting in specialized and relevant outputs for your business needs.
- **Azure OpenAI Models**: Provides pre-trained and customisable big language models for a variety of AI applications, including text generation, sentiment analysis, and language translation, with the option to tailor models to specific use cases.
- **Azure CloudShell**: Offers an online, browser-based shell for managing Azure resources and running scripts.Allows you to deploy, manage, and automate Azure services directly from your web browser, eliminating the need for local installations.
- **DALL-E**: DALL-E uses artificial intelligence technology to generate visuals from written descriptions.Enhances creativity by translating word inputs into distinct and coherent pictures.

## Getting Started with Lab

1. Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the lab guide bottom area to switch to different exercises of the lab guide.

   ![](../media/getting-started-page.png "Lab Environment")
   
1. To get the lab environment details, you can select the **Environment Details** tab. Additionally, the credentials will also be emailed to your email address provided during registration. You can start, stop, and restart virtual machines from the **Resources** tab.

   ![](../media/envdetails.png "Lab Environment")

## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
![](../media/1302024(4).png)

## Lab Validation

1. After completing the task, hit the **Validate** button under the Validation tab integrated within your lab guide. If you receive a success message, you can proceed to the next task, if not, carefully read the error message and retry the step, following the instructions in the lab guide.

   ![Inline Validation](../media/inline-validation.png)

1. If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com.

## Lab Guide Zoom In/Zoom Out

1. To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

   ![Manage Your Virtual Machine](../media/timer.png)

## Login to Azure Portal

1. In the JumpVM, click on Azure portal shortcut of Microsoft Edge browser which is created on desktop.

   ![](../media/azureportal_icon1.png "Lab Environment")
   
1. On **Sign into Microsoft Azure** tab you will see login screen, in that enter following email/username and then click on **Next**.
   
   * Email/Username: <inject key="AzureAdUserEmail"></inject>
   
     ![](../media/image7.png "Enter Email")
     
1. Now enter the following password and click on **Sign in**.
   
   * Password: <inject key="AzureAdUserPassword"></inject>
   
     ![](../media/image8.png "Enter Password")
     
1. If you see the pop-up **Action Required**, click **Ask Later**.

     ![](../media/asklater.png "Action required window")
     
    > If you are getting popup **save password**, then select **Save & Turn on** option.
       
1. If you see the pop-up **Stay Signed in?**, click **No**.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Cancel** to skip the tour.

1. Now you will see Azure Portal Dashboard, click on **Resource groups** from the Navigate panel to see the resource groups.

     ![](../media/select-rg.png "Resource groups")

1. Confirm you have a resource group **openai-<inject key="Deployment-id" enableCopy="false"/>** present as shown in the below screenshot. You need to use the **openai-<inject key="Deployment-id" enableCopy="false"/>** resource group throughout the entire process of lab execution.

     ![](../media/rg.png "Resource groups")
   

In this hands-on-lab, you will learn how Azure OpenAI models can generate and refine code and use the DALL-E model to create images from text prompts, showcasing AI's versatility in coding and creativity.

## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Click on the **Next** button from lower right corner to move on to the next page.

![](../media/msi-image1.png)

### Happy learning !
