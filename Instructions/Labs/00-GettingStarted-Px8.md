# Introduction to Azure OpenAI for NLP

### Overall Estimated Duration: 4 Hours

## Overview

Azure OpenAI Service brings the generative AI models developed by OpenAI to the Azure platform, enabling the development of powerful AI solutions with the security, scalability, and integration of Azure's cloud services. In this lab, you'll learn to provision Azure OpenAI as a resource and use Azure OpenAI Studio to deploy and explore OpenAI models. With Azure OpenAI, developers can create applications like chatbots and language models that excel in understanding natural human language. The service provides access to pre-trained AI models and a suite of APIs and tools for customizing and fine-tuning these models to meet specific application requirements. In this scenario, you'll assume the role of a software developer tasked with implementing an app to provide hiking recommendations using generative AI, demonstrating techniques applicable to any app utilizing Azure OpenAI APIs.

## Objective

In this hands-on lab, you will learn how to use OpenAI to create natural language solutions. You’ll start by setting up the OpenAI environment in Azure and exploring the basic features of OpenAI models for language processing. By the end of the lab, you’ll build and deploy a simple application that can process and respond to user input, while also learning how to enhance the model’s performance and output quality.

- **Get started with Azure OpenAI Service:** This hands-on lab aims to provision an Azure OpenAI resource and deploy a model. Explore the model's capabilities in the Completions playground, then interact with it using the Chat playground. Fine-tune responses by adjusting prompts and parameters, and leverage code generation to automate tasks.
- **Use Azure OpenAI SDKs in your App:** This hands-on lab aims to provision an Azure OpenAI resource, deploy a model, set up and configure an application in Cloud Shell, and then run the application, demonstrating the full lifecycle from resource creation to application deployment and execution.

## Pre-requisites

- Familiarity with Azure OpenAI Service, Azure CLI, and REST APIs
- Basic understanding of AI and machine learning concepts

## Architecture

The architecture flow for this task begins with provisioning an Azure OpenAI resource within your Azure subscription and deploying a pre-trained model using Azure OpenAI Studio. Next, you'll explore the model's capabilities in the Completions playground and test its conversational abilities in the Chat playground, experimenting with different prompts and parameters to customize responses. You'll also investigate the model's code-generation capabilities. In the application development phase, you'll set up your application environment in Azure Cloud Shell, configure the application to integrate with the deployed OpenAI model, and finally, run the application to provide hiking recommendations using generative AI.

## Architecture Diagram

 ![Access Your VM and Lab Guide](../media/arch-diag-new.png)

## Explanation of Components

1. **Azure OpenAI:** Azure OpenAI Service provides REST API access to OpenAI's powerful language models, and these models integrate with your data, enabling customized and secure interactions.
1. **Azure OpenAI Models:** Offers pre-trained and customizable large language models for various AI applications. These models allow for powerful AI-driven solutions by generating tailored and contextually relevant content based on well-crafted prompts.
1. **Azure CloudShell:** Azure CloudShell offers an integrated, browser-based shell experience for managing Azure resources. It provides a ready-to-use environment with pre-installed tools and access to both Bash and PowerShell.

## Getting Started with the Lab

Welcome to the **Introduction to Azure OpenAI for NLP** Workshop!. In this lab, you will learn how to use OpenAI models to create natural language solutions. You'll explore the basics and work on building and deploying applications that understand and process language. Let’s get started with the lab and explore the possibilities of AI.
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.
 
![Access Your VM and Lab Guide](../media/GS1.png)

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, you can navigate to the **Environment** tab.
 
![Explore Lab Resources](../media/GS3i.png)

## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![Use the Split Window Feature](../media/GS5i.png)
 
## Managing Your Virtual Machine
 
Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](../media/getting-started-eng-openai-3.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕: 100%** icon located next to the timer in the lab environment.

![Manage Your Virtual Machine](../media/nleg2.png)

## Lab Validation

After completing the task, hit the **Validate** button under the Validation tab integrated within your lab guide. If you receive a success message, you can proceed to the next task; if not, carefully read the error message and retry the step, following the instructions in the lab guide.

![Inline Validation](../media/GS6.png)

## Let's Get Started with Azure Portal
 
1. In the LabVM, click on the **Azure portal** shortcut of the Microsoft Edge browser, which is created on the desktop.

   ![Inicie el Portal de Azure](../media/GS2.png)
 
1. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](../media/GS3.png)
 
4. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![Enter Your Password](../media/GS4.png)
 
7. If prompted to **Stay Signed in**, you can click **No**.
 
    ![Use the Split Window Feature](../media/GS5.png)
    
8. If a **Welcome to Microsoft Azure** page appears, simply click **Cancel** to skip the tour.

    ![Welcome Page](../media/Welcome(Eng).png)

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![Start Your Azure Journey](../media/nleg6.png)

## Happy Learning!!
