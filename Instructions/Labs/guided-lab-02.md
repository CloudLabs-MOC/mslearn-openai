# Lab 01: Use Azure OpenAI SDKs in your App

### Estimated Duration: 120 Minutes

## Lab Overview

In the lab, you will perform the role of a software developer who has been tasked to implement an app that can use generative AI to help provide hiking recommendations. The techniques used in the exercise can be applied to any app that utilizes Azure OpenAI APIs.

With the Azure OpenAI Service, developers can create chatbots, language models, and other applications that excel at understanding natural human language. The Azure OpenAI provides access to pre-trained AI models, as well as a suite of APIs and tools for customizing and fine-tuning these models to meet the specific requirements of your application. In this exercise, you'll learn how to deploy a model in Azure OpenAI and use it in your application.

## Lab Objectives

In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Set up an application in Cloud Shell
- Task 4: Configure your application
- Task 5: Test your application

## Task 1: Provision an Azure OpenAI resource

In this task, you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **Azure portal**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)** from the result.

   ![](../media/azureai.png)

1. On  **Microsoft Foundry | Azure OpenAI** blade, select **Azure OpenAI (1)** from the left menu, click on **+ Create (2)** and select **Azure OpenAI (3)**

   ![](../media/va1.png)

1. Create an **Azure OpenAI** resource using the settings below, then click **Next (6)** three times, leaving all other options at their defaults.
    
    - Subscription: **Default Subscription (1)**
    
    - Resource group: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    
    - Region: **<inject key="Region" enableCopy="false"></inject> (3)**
    
    - Name: **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> (4)**
    
    - Pricing tier: **Standard S0 (5)**

    - Click **Next (6)** thrice to navigate to the **Review + submit** tab.
  
      ![](../media/clicknext.png)

1. Under the **Review + submit** tab, click on **Create**.

      ![](../media/clickcreate.png)

1. Wait for deployment to complete. Click on **Go to resource** to navigate to the deployed Azure OpenAI resource in the Azure portal.

      ![](../media/e1t1p5.png)

1. To capture the Keys and Endpoints values, on **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>** blade:

    - Navigate to **Keys and Endpoint (2)** under **Resource Management (1)**.
    
    - Click on **Show Keys (3)**.
    
    - Copy **Key 1 (4)** and ensure to paste it in a text editor such as notepad for future reference.
    
    - Finally copy the **Endpoint (5)** API URL by clicking on copy to clipboard. Paste it in a text editor such as notepad for later use.
    
        ![](../media/e1t1p5a.png "Keys and Endpoints")

<validation step="b6d08e8e-f2a3-4066-a698-2a324f4493dd" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

## Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. In the Azure OpenAI resource pane, click on **Go to Foundry portal**, which will navigate to **Microsoft Foundry**.

    ![](../media/va2.png)

1. Select the **Deployments (1)** from the left pane under **Shared resources**, click on **+ Deploy model (2)** and choose **Deploy base model (3)**.

    ![](../media/va3.png)

1. Search for **gpt-4.1-mini (1)** in the search bar, select **gpt-4.1-mini (2)** and click on **Confirm (3)**.

   ![](../media/va4.png)

1. Within the **Deploy gpt-4.1-mini** pop-up interface, enter the following details:

    - **Deployment name**: **text-turbo (1)**

    - **Deployment type**: **Standard (2)**

    - Click on **Customize**

    - **Model version upgrade policy**: Select **Upgrade once new default version becomes available (3)**

    - **Model version**: Choose **2025-04-14 (Default) (4)**

    - **Tokens per Minute Rate Limit**: **10K (5)**
        >**Note**: If you're unable to slide to 10K, click on the slider thumb and use your keyboard arrows (right/left) to adjust the token rate limit.

    - **Enable dynamic quota**: Ensure dynamic quota is **Enabled (6)**

    - Click on **Deploy (7)**

        ![](../media/deploy4.1.png)

1. This will deploy a model that you will be playing around with as you proceed.

<validation step="69a18560-a442-467a-be09-b5663806dd0a" />

> **Note:** Azure OpenAI includes multiple models, each optimized for a different balance of capabilities and performance. In this exercise, you'll use the **gpt-4.1-mini** model, which is a good model for summarizing and generating natural language and code. For more information about the available models in Azure OpenAI, see [Models](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) in the Azure OpenAI documentation.

## Task 3: Set up an application in Cloud Shell

In this task, you will set up a development environment using Azure Cloud Shell. You will clone the sample application repository, prepare the workspace, and open the code editor to begin integrating Azure OpenAI services.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/L2T2S1.png)

    >**Note:** If you can't find Cloud Shell, click on the **ellipsis (...) (1)** and then select **Cloud Shell (2)** from the menu.

    ![](../media/180625(14).png)

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**. If you don't see this option, skip the step.

    ![](../media/bash.png)

1. Within the **Getting started** page, select **Mount storage account (1)**, select your **Subscription (2)** from the dropdown and click **Apply (3)**.

   ![](../media/mountstrg.png)

1. Within the **Mount storage account** page, select **I want to create a storage account (1)** and click **Next (2)**.

   ![](../media/csanext.png)

1. Within the **Create storage account** page, enter the following details:

    - Subscription: Choose the **Default subscription (1)**.

    - Resource group: Select **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    
    - Region: **<inject key="Region" enableCopy="false" /> (3)**

    - Storage account name: **storage<inject key="DeploymentID" enableCopy="false"></inject> (4)**

    - File share: Create a new file share named **none (5)**

    - Click **Create (6)**

        ![](../media/csacreate.png)

1. Note that you can resize the cloud shell by dragging the separator bar at the top of the page, or by using the **&#8212;**, **&#9723;**, and **X** icons at the top right of the page to minimize, maximize, and close the pane. For more information about using the Azure Cloud Shell, see the [Azure Cloud Shell documentation](https://docs.microsoft.com/azure/cloud-shell/overview). 

1. Once the terminal opens, click on **Settings (1)** and select **Go to Classic version (2)**.

    ![](../media/classic.png)

1. Once the terminal starts, enter the below-mentioned command to download the sample application and save it to a folder called `azure-openai`.
    >**Tip**: You can right-click to paste in the terminal

    ```bash
   rm -r mslearn-openai -f
   git clone https://github.com/microsoftlearning/mslearn-openai mslearn-openai
    ```

    ![](../media/L2T2S8-1507.png)    
  
1. The files are downloaded to a folder named **mslearn-openai**. Navigate to the lab files for this exercise using the following command.

    ```bash
   cd mslearn-openai/Labfiles/01-app-develop
    ```

    >**Note**: Applications for both **C#** and **Python** have been provided, as well as a sample text file you'll use to test the summarization. Both apps feature the same functionality.

1. Open the built-in code editor, and observe the text file that you'll be summarizing with your model. Use the following command to open the lab files in the code editor.

    ```bash
    code .
    ```

      ![](../media/code-editor.png)

<validation step="4eb72f2c-5f15-42b7-9637-abdaf9e30be5" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

## Task 4: Configure your application

In this task, you will configure the application to connect with the Azure OpenAI resource. You will update configuration files with your environment credentials and implement the client logic to interact with the deployed model.

1. In the code editor, expand the **CSharp** or **Python** folder, depending on your language preference.

1. If you are using the **C#** language, kindly open the **CSharp.csproj** file and replace it with the following code and save the file using **Ctrl+S**.

   ```
   <Project Sdk="Microsoft.NET.Sdk">
   
   <PropertyGroup>
   <OutputType>Exe</OutputType>
   <TargetFramework>net9.0</TargetFramework>
   <ImplicitUsings>enable</ImplicitUsings>
   <Nullable>enable</Nullable>
   </PropertyGroup>
   
    <ItemGroup>
    <PackageReference Include="Azure.AI.OpenAI" Version="2.1.0" />
    <PackageReference Include="Microsoft.Extensions.Configuration" Version="8.0.*" />
    <PackageReference Include="Microsoft.Extensions.Configuration.Json" Version="8.0.*" />
    </ItemGroup>
   
    <ItemGroup>
      <None Update="appsettings.json">
        <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
       </None>
     </ItemGroup>
   
    </Project> 
   ```

1. Open the configuration file for your language

    - C#: `appsettings.json`
    
    - Python: `.env`
    
1. Update the configuration values to include the **endpoint** and **key** from the Azure OpenAI resource you created, as well as the model name that you deployed, `text-turbo` and then save the file by right-clicking on the blank space in the file text editor and hit **Save** or use **Ctrl+S**.

    - **C#:**
     
      ![](../media/nlp26.png)

    - **Python:**
     
      ![](../media/nlp27.png)

       > **Note:** You can get the Azure OpenAI endpoint and key values from the Azure OpenAI resource's **Key and Endpoint** section under **Resource Management**. Refer to `Task 1: Step 6`.

1. Navigate back to the Cloudshell and install the necessary packages for your preferred language:

    **C#:** 

    ```bash
    cd CSharp
    dotnet add package Azure.AI.OpenAI --version 2.1.0
    ```

    **Python:** 

    ```bash
    cd Python
    python -m venv labenv
    pip install python-dotenv openai==1.65.2 --user
    ```
    >**Note:** If you want to return to the previous folder to choose a different language, use `cd ..` command in the terminal.

1. Navigate to your preferred language folder, replace the comment **Add Azure OpenAI package** with the code to add the Azure OpenAI SDK library:

    **C#:** Program.cs

    ```csharp
    // Add Azure OpenAI packages
    using Azure.AI.OpenAI;
    using OpenAI.Chat;
    ```

     ![](../media/L2T3S6-1507.png) 

    **Python:** application.py

    ```python
    # Add Azure OpenAI package
    from openai import AsyncAzureOpenAI
    ```

     ![](../media/L2T3S6-py.png)

     Save the files by right-clicking on the blank space in the file text editor and hit **Save** or use **Ctrl+S**.

1.  In the application code for your language, find the comment **Configure the Azure OpenAI client**, and add code to configure the Azure OpenAI client:

    **C#:** Program.cs

    ```csharp
    // Configure the Azure OpenAI client
    AzureOpenAIClient azureClient = new (new Uri(oaiEndpoint), new ApiKeyCredential(oaiKey));
    ChatClient chatClient = azureClient.GetChatClient(oaiDeploymentName);
    ```

     ![](../media/L2T3S7-1507.png)  

    **Python:** application.py

    ```python
    # Configure the Azure OpenAI client
    client = AsyncAzureOpenAI(
       azure_endpoint = azure_oai_endpoint, 
       api_key=azure_oai_key,  
       api_version="2024-02-15-preview"
      )
    ```

     ![](../media/L2T3S7-py.png)   

      >**Note:** Make sure to indent the code by eliminating any extra white spaces after pasting it into the code editor.

    Save the files by right-clicking on the blank space in the file text editor and hit **Save** or use **Ctrl+S**.

1. In the function that calls the **Azure OpenAI model**, under the comment **Get response from Azure OpenAI**, add the code to format and send the request to the model.

    **C#:** Program.cs

    ```csharp
      // Get response from Azure OpenAI
      ChatCompletionOptions chatCompletionOptions = new ChatCompletionOptions()
      {
         Temperature = 0.7f,
         MaxOutputTokenCount = 800
      };
      
      ChatCompletion completion = chatClient.CompleteChat(
         [
             new SystemChatMessage(systemMessage),
             new UserChatMessage(userMessage)
         ],
         chatCompletionOptions
      );
      
      Console.WriteLine($"{completion.Role}: {completion.Content[0].Text}");
    ```

     ![](../media/L2T3S8-1507.png)      

    **Python:** application.py

    ```python
    # Get response from Azure OpenAI
      messages =[
         {"role": "system", "content": system_message},
         {"role": "user", "content": user_message},
      ]
      
      print("\nSending request to Azure OpenAI model...\n")
      
      # Call the Azure OpenAI model
      response = await client.chat.completions.create(
         model=model,
         messages=messages,
         temperature=0.7,
         max_tokens=800
      )
    ```

     ![](../media/L2T3S8-py.png)  

1. Before you can save the file, please make sure your code looks similar to the code provided below.

    **C#:** Program.cs
      
      ```CSharp
      // Implicit using statements are included
      using System.Text;
      using System.ClientModel;
      using System.Text.Json;
      using Microsoft.Extensions.Configuration;
      using Microsoft.Extensions.Configuration.Json;
      using Azure;
      
      // Add Azure OpenAI packages
          using Azure.AI.OpenAI;
          using OpenAI.Chat;
      
      // Build a config object and retrieve user settings.
      class ChatMessageLab
      {
      
      static string? oaiEndpoint;
      static string? oaiKey;
      static string? oaiDeploymentName;
          static void Main(string[] args)
      {
      IConfiguration config = new ConfigurationBuilder()
          .AddJsonFile("appsettings.json")
          .Build();
      
      oaiEndpoint = config["AzureOAIEndpoint"];
      oaiKey = config["AzureOAIKey"];
      oaiDeploymentName = config["AzureOAIDeploymentName"];
      
      //Initialize messages list
      
      do {
          // Pause for system message update
          Console.WriteLine("-----------\nPausing the app to allow you to change the system prompt.\nPress any key to continue...");
          Console.ReadKey();
          
          Console.WriteLine("\nUsing system message from system.txt");
          string systemMessage = System.IO.File.ReadAllText("system.txt"); 
          systemMessage = systemMessage.Trim();
      
          Console.WriteLine("\nEnter user message or type 'quit' to exit:");
          string userMessage = Console.ReadLine() ?? "";
          userMessage = userMessage.Trim();
          
          if (systemMessage.ToLower() == "quit" || userMessage.ToLower() == "quit")
          {
              break;
          }
          else if (string.IsNullOrEmpty(systemMessage) || string.IsNullOrEmpty(userMessage))
          {
              Console.WriteLine("Please enter a system and user message.");
              continue;
          }
          else
          {
              // Format and send the request to the model
      
              GetResponseFromOpenAI(systemMessage, userMessage);
          }
      } while (true);
      
      }
      
      // Define the function that gets the response from Azure OpenAI endpoint
      private static void GetResponseFromOpenAI(string systemMessage, string userMessage)  
      {   
          Console.WriteLine("\nSending prompt to Azure OpenAI endpoint...\n\n");
      
          if(string.IsNullOrEmpty(oaiEndpoint) || string.IsNullOrEmpty(oaiKey) || string.IsNullOrEmpty(oaiDeploymentName) )
          {
              Console.WriteLine("Please check your appsettings.json file for missing or incorrect values.");
              return;
          }
      
      // Configure the Azure OpenAI client
      AzureOpenAIClient azureClient = new (new Uri(oaiEndpoint), new ApiKeyCredential(oaiKey));
      ChatClient chatClient = azureClient.GetChatClient(oaiDeploymentName);
      
      
      // Get response from Azure OpenAI
      
      ChatCompletionOptions chatCompletionOptions = new ChatCompletionOptions()
      {
         Temperature = 0.7f,
         MaxOutputTokenCount = 800
      };
      
      ChatCompletion completion = chatClient.CompleteChat(
         [
             new SystemChatMessage(systemMessage),
             new UserChatMessage(userMessage)
         ],
         chatCompletionOptions
      );
      
      Console.WriteLine($"{completion.Role}: {completion.Content[0].Text}");
      
      
      
      }
      
      }
      ```
    
   **Python:** application.py

      ```Python
      import os
      import asyncio
      from dotenv import load_dotenv
      
      # Add Azure OpenAI package
      from openai import AsyncAzureOpenAI
      
      async def main(): 
          try: 
              # Get configuration settings 
              load_dotenv()
              azure_oai_endpoint = os.getenv("AZURE_OAI_ENDPOINT")
              azure_oai_key = os.getenv("AZURE_OAI_KEY")
              azure_oai_deployment = os.getenv("AZURE_OAI_DEPLOYMENT")
              
              # Configure the Azure OpenAI client
              client = AsyncAzureOpenAI(
                  azure_endpoint=azure_oai_endpoint, 
                  api_key=azure_oai_key,  
                  api_version="2024-02-15-preview"
              )
      
              while True:
                  # Pause the app to allow the user to enter the system prompt
                  print("------------------\nPausing the app to allow you to change the system prompt.\nPress enter to continue...")
                  input()
      
                  # Read in system message and prompt for user message
                  system_text = open(file="system.txt", encoding="utf8").read().strip()
                  user_text = input("Enter user message, or 'quit' to exit: ")
                  if user_text.lower() == 'quit' or system_text.lower() == 'quit':
                      print('Exiting program...')
                      break
      
                  # Format and send the request to the model
                  await call_openai_model(
                      system_message=system_text, 
                      user_message=user_text, 
                      model=azure_oai_deployment, 
                      client=client
                  )
      
          except Exception as ex:
              print(ex)
      
      # Define the function that will get the response from Azure OpenAI endpoint
      async def call_openai_model(system_message, user_message, model, client):
          # Get response from Azure OpenAI
          messages = [
              {"role": "system", "content": system_message},
              {"role": "user", "content": user_message},
          ]
          
          print("\nSending request to Azure OpenAI model...\n")
          
          # Call the Azure OpenAI model
          response = await client.chat.completions.create(
              model=model,
              messages=messages,
              temperature=0.7,
              max_tokens=800
          )
      
          print("Response:\n" + response.choices[0].message.content + "\n")
      
      if __name__ == '__main__': 
          asyncio.run(main())
      ```
    
1. To save the changes made to the file, right-click on the blank space in the file text editor and hit **Save**.

   >**Note:** Make sure to indent the code by eliminating any extra white spaces after pasting it into the code editor.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

## Task 5: Test your application

In this task, you will run the application and interact with the Azure OpenAI model using different system and user prompts. This hands-on testing will help you observe how prompt variations affect the model’s output.

1. In the folder of your preferred language, open the **system.txt** file. For each of the interactions, you'll enter the **System message** in this file and save it. Each iteration will pause first for you to change the system message.

1. In the interactive terminal pane, ensure the folder context is the folder for your preferred language. Then, enter the following command to run the application.

    ![](../media/csharpdir.png)  

    - **C#:** `dotnet run`

    ![](../media/pydir.png) 
    
    - **Python:** `python application.py`

      > **Tip:** You can use the **Maximize panel size** (**^**) icon in the terminal toolbar to see more of the console text.

1. In the terminal, it will ask you to enter a key to continue.

    ![](../media/170725(08).png)

1. For the first iteration, navigate to `System.txt` file **(1)**, enter the following prompts **(2)** and save the file:

   **System message:**
   
   ```
   You are an AI assistant
   ```

    ![](../media/va7.png)   
   
     >**Note:** System message should given in system.txt in C# or Python. Follow the same steps for the remaining prompts.
   
1. In the Enter User message, give the following message.

   **User message:**
   
   ```
   Write an intro for a new wildlife Rescue 
   ```

    ![](../media/va8.png)   

    >**Note:** User message should given in terminal in C# or Python. Follow the same steps for the remaining prompts.

1. Observe the output. The AI model will likely produce a good generic introduction to a wildlife rescue.

1. Next, enter the following prompts, which specify a format for the response:

   **System message:**
   
   ```
   You are an AI assistant helping to write emails
   ```

   **User message:**
   
   ```
   Write a promotional email for a new wildlife rescue, including the following:-Rescue name is Contoso - It specializes in elephants - Call for donations to be given at our website
   ```

1. Observe the output. This time, you'll likely see the format of an email with the specific animals included, as well as the call for donations.

1. Next, enter the following prompts that additionally specify the content:

   **System message:**
   
   ```
   You are an AI assistant helping to write emails
   ```

   **User message:**

   ```
   Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants, as well as zebras and giraffes - Call for donations to be given at our website - Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.
   ```
   
1. Observe the output, and see how the email has changed based on your clear instructions.   

1. Next, enter the following prompts where we add details about tone to the system message:

   **System message:**
   
   ```
   You are an AI assistant that helps write promotional emails to generate interest in a new business. Your tone is light, chit-chat oriented, and you always include at least two jokes.
   ```

   **User message:**

   ```
   Write a promotional email for a new wildlife rescue, including the following: - Rescue name is Contoso - It specializes in elephants, as well as zebras and giraffes - Call for donations to be given at our website - Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits..
   ```

1. Observe the output. This time, you'll likely see the email in a similar format, but with a much more informal tone. You'll likely even see jokes included!

1. Close the Cloudshell.

    ![](../media/va9.png)

## Summary

In this lab, you used your Azure OpenAI resource to build and test an application with the Azure OpenAI SDK by configuring the development environment, integrating required credentials, and running the sample app to observe how different prompts influence AI-generated responses.

### Congratulations on completing the lab!
