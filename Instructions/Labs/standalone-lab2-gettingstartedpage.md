# Lunch and Learn: Integrate Azure OpenAI into your App

### Overall Estimated Duration: 60 minutes

## Overview

The purpose of the lab is to enable you to effectively integrate Azure OpenAI Service into your applications, focusing on AI-driven functionalities. Through this lab, you will create and configure an Azure OpenAI resource, deploy and interact with a language model, and build a command-line application in Azure Cloud Shell. Additionally, you will learn to manage conversation history to enhance the contextual relevance of AI responses. This lab offers a professional, hands-on approach to understanding and applying Azure OpenAI capabilities in real-world scenarios.

## Objective

Understand how to deploy OpenAI models in Azure, configure them, and secure them with API keys. Gain skills in Command-line interfaces. By the end of this lab, you will be able to:

- **Azure OpenAI Integration**: Gain proficiency in integrating Azure OpenAI Service into your applications to leverage AI-driven functionalities.

- **Create and Configure Azure OpenAI Resources**: Gain experience in setting up and configuring an Azure OpenAI resource to facilitate the deployment of language models.

- **Deploy and Interact with Language Models**: Successfully deploy a language model and use a command-line application in Azure Cloud Shell to interact with it, understanding its role in processing natural language.

- **Manage Conversation History**: Learn how to manage conversation history to ensure that AI responses remain contextually relevant and meaningful.

- **Develop Practical AI-Powered Applications**: Acquire hands-on experience in building AI-powered applications, applying Azure OpenAI capabilities effectively in real-world scenarios.

## Prerequisites

You should have basic knowledge and understanding of the following:

- **Azure Portal**: The web interface for managing and provisioning Azure resources.
- **Azure services, including Azure OpenAI and Azure Cloud Shell**: Core Azure offerings for AI capabilities and command-line management.
- **Command-line interfaces**: Tools like Bash for executing commands.

## Architecture

This architecture allows users to leverage advanced AI capabilities by starting with the provision of an Azure OpenAI resource in the Azure portal. You will then deploy a model and set up a sample application using Cloud Shell. The application will be integrated with the Azure OpenAI model for text-based tasks. You'll test the application by sending prompts and reviewing responses. Finally, you'll enhance the application to manage conversation history for a more interactive experience.

## Architecture Diagram

![](../media/28-08-2024.png "Architecture Diagram")

## Explanation of Components

The architecture for this lab involves the following key components:

- **Resource Group**: A Resource Group is a container in Azure used to manage and organize related Azure resources. It facilitates access control, monitoring, and billing by grouping resources together and streamlining their management.

- **OpenAI Resource**: An OpenAI resource in Azure supports the deployment and management of OpenAI models. It provides the necessary infrastructure and APIs for utilizing advanced AI capabilities, such as natural language processing and generation.

- **Cloud Shell App**: A Cloud Shell app is an interactive, browser-based command-line tool provided by Azure. It enables you to manage and configure Azure resources directly from the portal, offering a convenient environment for executing scripts and commands.

## Getting Started with the Lab

Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the bottom of the lab guide to switch to different lab guide exercises.

## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **lab guide** will be right at your fingertips within your web browser.
 
![Access Your VM and Lab Guide](../media/itg1.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.
 
   ![Explore Lab Resources](../media/itg2.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.

   ![Use the Split Window Feature](../media/itg3.png)
 
## Managing Your Virtual Machine
 
Feel free to **start, stop, or restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](../media/itg-4.png)

## Lab Guide Zoom In/Zoom Out
 
To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![Manage Your Virtual Machine](../media/ZOOMINOUT.png)

## Lab Validation

1. After completing the task, hit the **Validate** button under the Validation tab integrated within your lab guide. If you receive a success message, you can proceed to the next task, if not, carefully read the error message and retry the step, following the instructions in the lab guide.

   ![Inline Validation](../media/itg5.png)

1. If you need any assistance, please contact us at Cloudlabs-support@spektrasystems.com.

## Lab Duration Extension

1. To extend the duration of the lab, kindly click the **Hourglass** icon in the top right corner of the lab environment. 

    ![Manage Your Virtual Machine](../media/gext.png)

    >**Note:** You will get the **Hourglass** icon when 10 minutes are remaining in the lab.

2. Click **OK** to extend your lab duration.
 
   ![Manage Your Virtual Machine](../media/gext2.png)

3. If you have not extended the duration prior to when the lab is about to end, a pop-up will appear, giving you the option to extend. Click **OK** to proceed.

## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the Azure Portal icon as shown below:

   ![Launch Azure Portal](../media/sc900-image(1).png)

2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](../media/sc900-image-1.png)
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![Enter Your Password](../media/sc900-image-2.png)
 
4. If prompted to stay signed in, you can click **No**.
 
5. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **Cancel** to skip the tour.
  
   ![Click on cancel](../media/imageae.png)

## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: Cloudlabs-support@spektrasystems.com

- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.
 
   ![Start Your Azure Journey](../media/sc900-image(3).png)

### Happy Learning!!
