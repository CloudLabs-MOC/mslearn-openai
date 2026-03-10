
# Develop Generative AI solutions with Azure OpenAI Service

### Overall Estimated Duration: 2 Hours

## Overview

This lab explores the capabilities of Azure OpenAI Service by working with Retrieval-Augmented Generation (RAG) and content filtering. You will connect your own data to Azure OpenAI using Azure AI Search and Blob Storage, interact with a model grounded in your data, and configure and run an application in Cloud Shell. Additionally, you will examine how Azure OpenAI content filters help prevent harmful or offensive outputs and learn how to review and configure content filtering settings to support responsible AI practices.

## Objective

In this lab, you will gain hands-on experience with Azure OpenAI resources. You will provision resources and deploy models, connect and interact with your own data in the chat playground, set up, configure, and run applications using Cloud Shell, and finally generate natural language responses while applying content filtering to manage and regulate AI-generated outputs. By the end of this lab, you will be able to:

- **Add your data for RAG using Azure OpenAI Service:** This hands-on exercise will help you integrate your data with the Azure OpenAI Service for Retrieval-Augmented Generation (RAG) to improve AI responses. Participants will integrate data into the Azure OpenAI Service to boost AI-powered retrieval and generation.

- **Explore content filters in Azure OpenAI:** This hands-on exercise demonstrates how to construct and maintain content filters in Azure OpenAI to control and refine generated outputs. Participants will learn about and implement content filters in Azure OpenAI to control and refine created material.


## Pre-requisites

- **Development Skills:** Basic programming knowledge and experience with APIs and SDKs.

- **AI Concepts:** Understanding prompt engineering and code development.

- **Content Management:** Understanding data integration for RAG and content filtering techniques.

## Architecture

The architecture utilizes Azure OpenAI Service to provision resources, deploy models, and configure an application in Cloud Shell. It involves setting up, testing, and running the application, enabling AI-driven solutions powered by Azure's scalability and security.

## Architecture Diagram

 ![](../media/l6-arch.png)

 ![](../media/l7-arch.png)

## Explanation of Components

The architecture for this lab involves the following key components:

- **Azure OpenAI Resource:** Provision an Azure OpenAI resource to access OpenAI’s advanced AI models, enabling integration with custom applications.

- **Model Deployment:** Deploy an OpenAI model to access and utilize its functionality for testing and application use cases.

- **Chat Behavior Exploration:** Observe the normal chat behavior without adding custom data, interacting with the model's default capabilities.

- **Data Integration:** Connect your own data to the chat playground to ground the model’s responses in your custom content.

- **Chat with Data-Driven Model:** Interact with a model grounded in your own data, enhancing the relevance and accuracy of the responses.

- **Application Configuration:** Configure the application to ensure smooth integration with Azure OpenAI services and meet specific requirements.

- **Run the Application:** Execute the application to validate the image generation functionality and confirm proper interaction with the deployed model.

- **Natural Language Output Generation:** Generate natural language output using the deployed model to process and understand data, enhancing the application’s capabilities.

## Getting Started with Lab

Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the lab guide bottom area to switch to different exercises of the lab guide.

## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and the **Guide** will be right at your fingertips within your web browser.

   ![](../media/l5-labvm.png "Lab Environment")

## Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

   ![Manage Your Virtual Machine](../media/l5-zoom.png)

## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

   ![](../media/g2.png)

## Utilizing the Split Window Feature
 
For your convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the top right corner.

![](../media/g3.png)
  
## Managing Your Virtual Machine
 
Feel free to **Start, Restart, or Stop (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](../media/g4.png)

## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the **Azure Portal** icon as shown below:
 
      ![Launch Azure Portal](../media/sc900-image(1).png)
    
2. You'll see the **Sign in to continue to Microsoft Azure** tab. Here, enter your credentials:
 
    - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](../media/sc900-image-1.png)
 
3. Next, provide your password:
 
    - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![](../media/tpwrd.png)
 
4. In the **Stay signed in?** pop-up, click **No**.

    ![](../media/staysign.png)
 
## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: cloudlabs-support@spektrasystems.com

- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

![](../media/l5-next.png)

## Happy Learning!!
