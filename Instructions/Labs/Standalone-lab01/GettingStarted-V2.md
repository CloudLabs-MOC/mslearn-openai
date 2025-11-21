# Lunch and Learn: Get started with Azure OpenAI Service

### Overall Estimated Duration: 60 Minutes

## Overview

This lab introduces you to Azure OpenAI Service, a powerful platform that integrates OpenAI's generative AI models with the Azure cloud environment. Designed to introduce you to its core concepts and capabilities, this lab will guide you through provisioning a resource, deploying models, and interacting with various features. Learn to set up and configure an Azure OpenAI resource, deploy models, experiment with the Chat playgrounds, and acquire foundational skills in utilizing Azure's infrastructure for developing and refining AI-powered applications.

## Objective

Understand how to deploy Azure OpenAI Service, enabling you to integrate and explore OpenAI's advanced models within the secure and scalable Azure platform. By the end of this lab, you will be able to:

- **Get started with Azure OpenAI Service:** Gain experience in provisioning and configuring an Azure OpenAI resource, deploying an AI model (e.g., gpt-4o-mini), exploring model interactions in the Chat playgrounds, experimenting with prompts and parameters for fine-tuning, and leveraging the model's capabilities for code generation.

## Pre-Requisites

Participants should have basic knowledge and understanding of the following :

- **Azure Portal:** For managing and provisioning Azure resources.
- **Azure AI Foundry:** For deploying models, configuring and experimenting with their capabilities, including features such as the Chat playgrounds.

## Architecture

This architecture allows users to leverage Azure's cloud infrastructure to deploy and interact with advanced AI models.
The flow of the lab will be to use an existing Resource Group, then create and deploy an OpenAI model in Azure. Next, explore the model in the playground and generate code using AI. Through the Azure Portal, users manage their resources, while Azure AI Foundry provides the tools needed to deploy and test these models. Chat playgrounds within Azure AI Foundry enable hands-on experimentation and refinement, facilitating the development of robust AI-powered applications.

## Architecture Diagram:

![](./media/archdiagram1.png)

## Explanation of Components

- **Azure Portal:** Central interface for provisioning and managing Azure OpenAI resources, including model deployment settings and resource configuration.

- **Resource Group:** This is a container in Azure that holds related resources for your project. It helps us organize and manage services like your OpenAI model in one place.

- **Azure OpenAI Service:** The managed service that brings OpenAI’s generative models, such as GPT-4o-mini, into the Azure ecosystem. It provides secure, scalable endpoints to use language models for tasks like chat, summarization, Q\&A, or code generation, while also supporting enterprise-grade features such as quotas, authentication, and monitoring.

- **Azure AI Foundry:** A unified workspace where you deploy, test, and interact with AI models. It provides tools like the Chat Playground for experimenting with conversational use cases, and configuration options for prompts, parameters, and system instructions. Foundry also integrates with observability and monitoring features, making it the primary interface for fine-tuning and experimenting with deployed models.

## Getting Started with the Lab

Welcome to your Get Started with Azure OpenAI Service Workshop! We've prepared a seamless environment for you to explore and learn about Azure services. Let's begin by making the most of this experience.
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and the **Guide** will be right at your fingertips within your web browser.
 
![](./media/guide.png)

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

   ![Manage Your Virtual Machine](./media/zoominout.png)

## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
![](./media/envt.png)
 
## Utilizing the Split Window Feature
 
For your convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the top right corner.
 
![](./media/splitwin.png)
 
## Managing Your Virtual Machine
 
Feel free to **Start, Restart, or Stop (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](./media/resourcetab.png)

## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the **Azure Portal** icon as shown below:
 
      ![Launch Azure Portal](./media/sc900-image(1).png)
    
2. You'll see the **Sign in to continue to Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](./media/sc900-image-1.png)
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![](./media/tpwrd.png)

4. In the **Stay signed in?** pop-up, click **No**.

   ![](./media/2025-07-08(1).png)
 
## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com

- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![Start Your Azure Journey](./media/nextpage.png)

## Happy Learning!!
