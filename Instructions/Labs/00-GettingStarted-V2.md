#  Get Started with Microsoft Foundry and Build Natural Language Solution

### Estimated Duration: 4 Hours

## 📘 Lab Scenario

You have recently joined **Contoso**, an organization that wants to bring generative AI into its internal learning platform and its customer outreach both of which rely today on static, hand-written content. Before any application is built, your manager asks you to evaluate the platform itself. Acting as an **AI developer**, you'll provision a **Microsoft Foundry** resource in the Azure subscription, deploy a model, and validate its behaviour hands-on in the **Microsoft Foundry portal** playground shaping the assistant's persona with instructions and few-shot examples, controlling response length and depth with parameters such as *max completion tokens* and *reasoning effort*, and confirming the model can generate usable code.

With the evaluation approved, you step into the role of a **software developer** on the delivery project: an app that uses generative AI to provide **hiking recommendations** to customers, adaptable later to any other content the marketing and outreach teams need. Starting from the Foundry resource and model deployment you created, you'll prepare a development environment in **Azure Cloud Shell**, wire up a starter application in either **C#** or **Python** using the **OpenAI SDK** against Foundry's OpenAI-compatible endpoint, and tune its behaviour by adjusting the **system message** and **user prompts** across several iterations the same path you would follow for any app built on Foundry APIs.

## 📖 Lab Overview

**Microsoft Foundry** is Microsoft's unified platform for building AI solutions on Azure, bringing generative AI models including the models developed by Microsoft Foundry  together with the security, scalability, and service integration of Azure's cloud services. In this lab, you'll learn to provision a Microsoft Foundry resource and use the Microsoft Foundry portal to deploy and explore Microsoft Foundry  models. With Foundry, developers can create applications like chatbots and copilots that excel in understanding natural human language. The platform provides access to a catalog of pre-trained models along with a suite of APIs and tools for customizing and evaluating those models to meet specific application requirements. In this scenario, you'll assume the role of a software developer tasked with implementing an app to provide hiking recommendations using generative AI, demonstrating techniques applicable to any app utilizing Foundry APIs.

## 🎯 Lab Objectives

In this hands-on lab, you will learn how to use Microsoft Foundry  models in Microsoft Foundry to create natural language solutions. You’ll start by setting up your Foundry environment in Azure and exploring the basic features of Microsoft Foundry  models for language processing. By the end of the lab, you’ll build and deploy a simple application that can process and respond to user input, while also learning how to enhance the model’s performance and output quality.

- **Get started with Microsoft Foundry:** This hands-on lab aims to provision a Microsoft Foundry resource and deploy an Microsoft Foundry  model. Explore the model's capabilities in the Chat playground, fine-tune responses by adjusting instructions, prompts, and parameters, and leverage code generation to automate tasks.
- **Use Microsoft Foundry OpenAI SDKs in your App:** This hands-on lab aims to review a Microsoft Foundry resource and its deployed model, set up and configure an application in Cloud Shell, and then run the application, demonstrating the full lifecycle from resource creation to application deployment and execution.

## ⚙️ Pre-requisites

- Familiarity with Microsoft Foundry, Azure CLI, and REST APIs
- Basic understanding of AI and machine learning concepts

- An active Microsoft Azure subscription to deploy and manage Azure resources.
- An Azure Entra ID user account with sufficient permissions to create and manage resources within the Azure subscription.
- Familiar with Python & CSharp programming language.

## 🏗️ Architecture

The architecture flow for this task begins with provisioning a Microsoft Foundry resource within your Azure subscription and deploying a pre-trained Microsoft Foundry  model using the Microsoft Foundry portal. Next, you'll test the model's conversational abilities in the Chat playground, experimenting with different instructions, prompts, and parameters to customize responses. You'll also investigate the model's code-generation capabilities. In the application development phase, you'll set up your application environment in Azure Cloud Shell, configure the application to integrate with the deployed model through its Foundry endpoint and key, and finally, run the application to provide hiking recommendations using generative AI.

## 🖼️ Architecture Diagram

 ![Architecture Diagram](../media/architecture-gs-foundry.png)

## 🔍  Explanation of Components

1. **Microsoft Foundry:** Microsoft Foundry is the unified platform for building AI solutions on Azure. It provides REST API access to powerful language models and the tooling to deploy, test, and integrate them with your data, enabling customized and secure interactions.
1. **Microsoft Foundry model catalog**: A single searchable catalog of pre-trained and customizable models you can deploy from the Microsoft Foundry portal, spanning chat and reasoning models from the GPT family, embedding models such as **text-embedding-3-large** for search and retrieval scenarios, image generation models, and open models from partners like **Meta, Mistral, and DeepSeek**. In this lab you deploy the **gpt-5.4** chat completion model from the catalog and use it in both the Chat playground and your application, generating tailored and contextually relevant content based on well-crafted prompts.
1. **Microsoft Foundry portal:** Provides a browser-based workspace for discovering models, deploying them, and testing them interactively in the playground before you call them from your own application code.
1. **Azure CloudShell:** Azure CloudShell offers an integrated, browser-based shell experience for managing Azure resources. It provides a ready-to-use environment with pre-installed tools and access to both Bash and PowerShell.

## 🚀 Getting Started with the Lab

Welcome to the **Get Started with Microsoft Foundry and Build Natural Language Solution** Workshop!. In this lab, you will learn how to use Microsoft Foundry  models to create natural language solutions. You'll explore the basics and work on building and deploying applications that understand and process language. Let’s get started with the lab and explore the possibilities of AI.
 
## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.
 
![Access Your VM and Lab Guide](../media/new-gs-labguide.png)

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, you can navigate to the **Environment** tab.
 
![Explore Lab Resources](../media/env-oai.png)

## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![Use the Split Window Feature](../media/split-tab.png)
 
## Managing Your Virtual Machine
 
Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](../media/lab-resources-op.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕** icon located next to the timer in the lab environment.

![Manage Your Virtual Machine](../media/lab-page-in.png)

## Resize the Virtual Machine View
Use the **slider (three vertical dots)** located between the **Virtual Machine** and the **Lab Guide** panes to adjust the display size, allowing you to customize the layout based on your preference.

![Resize the Virtual Machine View](../media/resize-vm-guide-2.png)

## Lab Validation

After completing the task, hit the **Validate** button under the Validation tab integrated within your lab guide. If you receive a success message, you can proceed to the next task; if not, carefully read the error message and retry the step, following the instructions in the lab guide.

![Inline Validation](../media/task-1-validation.png)

## Let's Get Started with Azure Portal
 
1. In the LabVM, click on the **Azure portal** shortcut of the Microsoft Edge browser, which is created on the desktop.

   ![Inicie el Portal de Azure](../media/sc900-image(1).png)
 
1. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](../media/sc900-image-1.png)
 
4. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![Enter Your Password](../media/sc900-image-2.png)
 
7. If prompted to **Stay Signed in**, you can click **No**.
 
8. If a **Welcome to Microsoft Azure** page appears, simply click **Cancel** to skip the tour.

## 📞 Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![Start Your Azure Journey](../media/nleg6.png)

## 🎉 Happy Learning!!
