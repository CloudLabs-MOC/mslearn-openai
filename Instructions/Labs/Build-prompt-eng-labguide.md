# Lab 02: Utilize prompt engineering in your app
### Estimated Duration: 60 Minutes

## Lab Overview

In the lab, you will perform the role of a software developer working on a wildlife marketing campaign. You are exploring how to use generative AI to improve advertising emails and categorize articles that might apply to your team. The prompt engineering techniques used in the exercise can be applied similarly for a variety of use cases.

When working with the Azure OpenAI Service, how developers shape their prompt greatly impacts how the generative AI model will respond. Azure OpenAI models are able to tailor and format content if requested in a clear and concise way. In this lab, you'll learn how different prompts for similar content help shape the AI model's response to better satisfy your requirements.

## Lab Objectives
In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Apply prompt engineering in the chat playground
- Task 4: Configure your application
- Task 5: Run your application

## Task 1: Provision an Azure OpenAI resource

In this task, you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. On the Azure portal, type **Azure OpenAI (1)** in the search box and select **Azure OpenAI (2)** from the results.

   ![](../media/gg_ex2_1_1.png)

1. In the **AI Foundry | Azure Open AI** page, under the **Use with AI Foundry** section, select **Azure OpenAI (1)** from the left pane. Then, click **+ Create (2)** at the top to provision a new Azure OpenAI resource.

   ![](../media/gg_ex2_1_2.png)

1. In the **Create Azure OpenAI** pane, configure a new **Azure OpenAI** resource using the following settings:

    - **Subscription:** Default - Pre-assigned subscription **(1)**.
    - **Resource group:** openai-<inject key="Deployment-ID" enableCopy="false"></inject> **(2)**
    - **Region:** Select **<inject key="Region" enableCopy="false"/>** **(3)**
    - **Name:** OpenAI-Lab01-<inject key="Deployment-ID" enableCopy="false"></inject> **(4)**
    - **Pricing tier:** Standard S0 **(5)**
    -  Click on **Next** **(6)**
  
       ![](../media/create-openai-2107.png "Create Azure OpenAI resource")

       >**Note:** Make sure you are deploying OpenAI resource in **France Central** Region.

1. Click **Next** twice to navigate to the **Review + submit** tab, then click **Create** to deploy the Azure OpenAI resource.

   ![](../media/create-openai2-2107.png)

1. Wait for deployment to complete. Then go to the deployed Azure OpenAI resource in the Azure portal by clicking on **Go to resource** button.

   ![](../media/gg_ex2_1_5.png)

1. In the **Azure OpenAI** resource, under the **Resource Management** section, to capture the Keys and Endpoints values, on **OpenAI-Lab01-<inject key="Deployment-ID" enableCopy="false"></inject>** blade:
      - Select **Keys and Endpoint (1)** under **Resource Management**.
      - Click on **Show Keys (2)**.
      - Copy **Key 1 (3)** and ensure to paste it into a text editor such as Notepad for future reference.
      - Finally, copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as Notepad for later use.

        ![](../media/gs_1_12.png "Keys and Endpoints")

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at Cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="500ab73f-41d7-4883-ab2c-110281939c65" />

## Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. On the Azure portal, type **Azure OpenAI (1)** in the search box and select **Azure OpenAI (2)** from the results.

   ![](../media/gg_ex2_1_7.png)

1. On **AI Foundry | Azure OpenAI** blade under the **Use with AI Foundry** section, select **Azure OpenAI (1)** from the left pane and select **OpenAI-Lab01-<inject key="Deployment-ID" enableCopy="false"></inject>** **(2)**.

   ![](../media/T2S2-2107.png)

1. In the Azure OpenAI resource page, click on the **Overview (1)** page and click on **Go to Azure AI Foundry portal (2)**. It will navigate to the **Azure AI Foundry portal**.
    
   ![](../media/gg_ex2_1_9.png)

1. In the Azure AI Foundry portal, under **Shared resources**, select **Deployments (1)** from the left pane. Click on **Deploy model (2)** and choose **Deploy base model (3)** from the dropdown.

   ![](../media/gg_ex2_1_11.png)

1. In the **Select a model** window, search for **gpt-4.1-mini (1)**, then select the **gpt-4.1-mini (Chat completion) (2)** model from the list. Click **Confirm (3)** to proceed with the deployment.

   ![](../media/L2T2S5.png)

1. On the **Deploy gpt-4.1-mini** screen, click **Customize** to modify deployment details.

   ![](../media/L2T2S6.png)

1. Within the **Deploy model** interface, enter the following details:
    - **Deployment name:** text-turbo **(1)**
    - **Deployment type:** GlobalStandard **(2)**
    - **Model version:** 2025-04-14(Default) **(3)**
    - **Tokens per Minute Rate Limit (thousands):** 10K **(4)**
    **Deploy** **(5)**

        >**Note:** Click on the customize and collapse button to expand the other options.

        ![](../media/L2T2S7.png)

        >**Note:** If you encounter an issue indicating that no model is found, please revert to the old version and attempt to deploy the model again. You can switch back to the new version once it's deployed.

        > **Note:** You can ignore the "Failed to fetch deployments quota information" notification.
        
        > **Note:** Each Azure OpenAI model is optimized for a different balance of capabilities and performance. We'll use the **3.5 Turbo** model series in the **GPT-3** model family in this exercise, which is highly capable of language understanding. This exercise only uses a single model; however, deployment and usage of other models you deploy will work in the same way.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at Cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="5b357640-1ad5-4345-a277-affb04231f21" />

## Task 3: Apply prompt engineering in chat playground

In this task, you will explore how prompt engineering impacts model behavior in the Azure AI Foundry Playground. You'll experiment with prompt styles, system messages, and example-based guidance to generate structured Python code and improve content classification accuracy.

1. In [Azure AI Foundry](https://oai.azure.com/?azure-portal=true), navigate to the **Chat** under **Playgrounds** section in the left pane.

   ![](../media/gg_ex2_1_15.png)

1. In the **Setup** section at the top, select **text-turbo (version:0125)** **(1)**, input `You are a helpful AI assistant` **(2)** as the model's instructions and context, then click on **Apply changes (3)**. Finally, click on **Continue (4)** in the pop-up.

   ![](../media/17022025(9).png)

   ![](../media/gg_ex2_1_16.png)

1. Scroll down and in the **Chat session** section, enter the below prompt **(1)** and click **Send (2)**.

   ```code
   1. Create a list of animals
   2. Create a list of whimsical names for those animals
   3. Combine them randomly into a list of 25 animal and name pairs
   ```
      ![](../media/gg_ex2_1_18.png)

   >**Note:** Kindly refresh the screen in case you encounter any error message and perform the above step again.

1. The model will likely respond with an answer to satisfy the prompt, split into a numbered list. This is a good response, but not what we're looking for.

   ![](../media/17022025(10).png)

1. Next in the selected **text-turbo (version:0125) (1)** deployment, update the system message to include instructions `You are an AI assistant helping write Python code. Complete the app based on the provided comments **(2)**. Click **Apply changes** **(3)** and subsequently click on **Continue (4)** in the pop-up.

   ![](../media/17022025(11).png)

   ![](../media/gg_ex2_1_17.png)

1. Format the instructions as Python comments. Send the following prompt to the model.

   ```code
   # 1. Create a list of animals
   # 2. Create a list of whimsical names for those animals
   # 3. Combine them randomly into a list of 25 animal and name pairs
   ```

1. The model should correctly respond with complete Python code, doing what the comments requested.

1. Next, we'll see the impact of a shot prompt when attempting to classify articles. Return to the system message, enter `You are a helpful AI assistant` again, click on **Apply changes**, and subsequently click on **Continue**. This will create a new chat session.

1. Send the following prompt to the model.

   ```code
   Severe drought likely in California

   Millions of California residents are bracing for less water and dry lawns as drought threatens to leave a large swath of the region with a growing water shortage.
   
   In a remarkable indication of drought severity, officials in Southern California have declared a first-of-its-kind action limiting outdoor water use to one day a week for nearly 8 million residents.
   
   Much remains to be determined about how daily life will change as people adjust to a drier normal. But officials are warning the situation is dire and could lead to even more severe limits later in the year.
   ```

1. The response will likely be some information about the drought in California. While not a bad response, it's not the classification we're looking for.

1. In the **Setup** section, click **+ Add section (1)**, select **Examples (2)** from the dropdown, and add the following example.

    ![](../media/gg_ex2_1_19.png)

1. In the **Examples** section, add a sample input provided below **User (1)** and add the expected response provided below **Assistant (2)**.

    **User:**

    ```code
    New York Baseballers Win Big Against Chicago

    New York Baseballers mounted a big 5-0 shutout against the Chicago Cyclones last night, solidifying their win with a 3-run homerun late in the bottom of the 7th inning.

    Pitcher Mario Rogers threw 96 pitches with only two hits for New York, marking his best performance this year.

    The Chicago Cyclones' two hits came in the 2nd and the 5th innings, but they were unable to get the runner home to score.
    ```

    **Assistant:**

    ```code
    Sports
    ```

    ![](../media/gg_ex2_1_20.png)

1. Click **+ Add section (1)** again, select **Examples (2)** from the dropdown, and add another example with the provided text.

    ![](../media/gg_ex2_1_19.png)

    **User:**

    ```code
    Joyous moments at the Oscars

    The Oscars this past week were quite something!

    Though a certain scandal might have stolen the show, this year's Academy Awards were full of moments that filled us with joy and even moved us to tears.
    These actors and actresses delivered some truly emotional performances, along with some great laughs, to get us through the winter.

    From Robin Kline's history-making win to a full performance by none other than Casey Jensen herself, don't miss tomorrow's rerun of all the festivities.
    ```

    **Assistant:**

    ```code
    Entertainment
    ```

1. Select **Apply changes** to the assistant setup to save the updates.

    ![](../media/gg_ex2_1_21.png)

1. In the **Chat session** section, now again send the same prompt about the California drought, provided here again for convenience.

    ```code
    Severe drought likely in California

    Millions of California residents are bracing for less water and dry lawns as drought threatens to leave a large swath of the region with a growing water shortage.

    In a remarkable indication of drought severity, officials in Southern California have declared a first-of-its-kind action limiting outdoor water use to one day a week for nearly 8 million residents.

    Much remains to be determined about how daily life will change as people adjust to a drier normal. But officials are warning that the situation is dire and could lead to even more severe limits later in the year.
    ```

1. This time, the model should respond with an appropriate classification, even without instructions.

    > **Note:** If you notice a delay in the response, try clearing the chat and starting again.

## Task 4: Configure your application

In this task, you will complete key parts of the provided C# or Python application to enable it to use your Azure OpenAI resource with asynchronous API calls, as both apps feature the same functionality.

1. On the Lab VM desktop, right-click the **Visual Studio Code (1)** icon and select **Open (2)** from the context menu.

   ![](../media/gg_ex2_1_22.png)

1. In Visual Studio Code, click on **File (1)** in the top menu and select **Open Folder... (2)** to browse and open the desired project directory.

      ![](../media/gg_ex2_1_23.png)

1. In the file browser, navigate to **`C:/Users/azureuser` (1)**, select the **azure-openai (2)** folder, and click **Select Folder (3)** to open it in Visual Studio Code.

   ![](../media/gg_ex2_1_24.png)
    
1. In the **EXPLORER** pane, expand the **Labfiles (1)** folder and select **03-prompt-engineering (2)** to view the project contents.

   ![](../media/gg_ex2_1_26.png)

   > **Note:** Applications for both C# and Python have been provided, as well as a text files that provide the prompts. Both apps feature the same functionality.

1. After expanding the **03-prompt-engineering** folder, open either the **CSharp** or **Python** subfolder based on your preferred programming language. Each folder contains language-specific files to integrate **Azure OpenAI** functionality into the app.

   ![](../media/gg_ex2_1_27.png)

1. Open the configuration file for your language.

    - C#: `appsettings.json`
    
    - Python: `.env`
    
1. Update the configuration values to include the **endpoint**, **key**, and the deployed model name `text-turbo` from your Azure OpenAI resource.  
   Then, right-click the file in the left pane and click **Save** to apply the changes.

   - **C# :** Update the values in **appsettings.json (1)** as shown **(2)**.  

     ![](../media/gg_ex2_1_28.png)

   - **Python :** Update the values in **.env (1)** as shown **(2)**.

     ![](../media/gg_ex2_1_29.png)

1. In the **EXPLORER** pane, right-click on the **03-prompt-engineering (1)** folder and select **Open in Integrated Terminal (2)** to launch a terminal in the project directory.

   ![](../media/gg_ex2_1_30.png)

     **C#:**

    ```
    cd CSharp
    irm https://dot.net/v1/dotnet-install.ps1 | iex
    ```

    **Python**
    ```bash
    cd Python
    ```
    > **Note:** Once the Python packages are installed, restart VS Code.

1. After restarting VS Code following the installation of Python packages, open a new terminal and run the following command to install the dotenv package.

    **Python**

    ```bash
    pip install python-dotenv
    ```

1. Enter the following command to add the `Azure.AI.OpenAI` NuGet package to your project, which is necessary for integrating with Azure OpenAI services.

     **C#:**

    ```
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.14
    ```

    **Python**

    ```bash
    pip install openai==1.55.3
    ```

1. Navigate to your preferred language folder, open the main code file, and add the necessary import for the Azure OpenAI package.

   - **C# (1):** Select the **Program.cs (2)** file inside the **CSharp** folder and add the following line at the top **(3)**:
     ```csharp
     // Add Azure OpenAI package
     using Azure.AI.OpenAI;
     ```
     ![](../media/gg_ex2_1_31.png)

   - **Python (1):** Select the **prompt-engineering.py (2)** file inside the **Python** folder and add the following line at the top **(3)**:
     ```python
     # Add Azure OpenAI package
     from openai import AsyncAzureOpenAI
     ```
     ![](../media/gg_ex2_1_32.png)

1. Open up the application code for your language and add the necessary code for configuring the client.

    **C#:** Program.cs

    ```csharp
   // Configure the Azure OpenAI client
   OpenAIClient client = new OpenAIClient(new Uri(oaiEndpoint), new AzureKeyCredential(oaiKey));
    ```

    **Python:** prompt-engineering.py

   ```python
    # Configure the Azure OpenAI client
    client = AsyncAzureOpenAI(
        azure_endpoint = azure_oai_endpoint, 
        api_key=azure_oai_key,  
        api_version="2024-02-15-preview"
        )
    ```

1. In the function that calls the Azure OpenAI model, add the code to format and send the request to the model.

    **C#:** Program.cs

    ```csharp
           // Format and send the request to the model
         var chatCompletionsOptions = new ChatCompletionsOptions()
         {
             Messages =
             {
                 new ChatRequestSystemMessage(systemMessage),
                 new ChatRequestUserMessage(userMessage)
             },
             Temperature = 0.7f,
             MaxTokens = 800,
             DeploymentName = oaiDeploymentName
         };
         
         // Get response from Azure OpenAI
         Response<ChatCompletions> response = await client.GetChatCompletionsAsync(chatCompletionsOptions);
    ```

    **Python:** prompt-engineering.py

   ```python
    # Format and send the request to the model
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

1. The  modified code should look as shown below:

    **C#**
      
      ```csharp
        // Implicit using statements are included
         using System.Text;
         using System.Text.Json;
         using Microsoft.Extensions.Configuration;
         using Microsoft.Extensions.Configuration.Json;
         using Azure;
         
         // Add Azure OpenAI package
         using Azure.AI.OpenAI;
         
         // Build a config object and retrieve user settings.
         IConfiguration config = new ConfigurationBuilder()
             .AddJsonFile("appsettings.json")
             .Build();
         string? oaiEndpoint = config["AzureOAIEndpoint"];
         string? oaiKey = config["AzureOAIKey"];
         string? oaiDeploymentName = config["AzureOAIDeploymentName"];
         
         bool printFullResponse = false;
         
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
                 await GetResponseFromOpenAI(systemMessage, userMessage);
             }
         } while (true);
         
         async Task GetResponseFromOpenAI(string systemMessage, string userMessage)  
         {   
             Console.WriteLine("\nSending prompt to Azure OpenAI endpoint...\n\n");
         
             if(string.IsNullOrEmpty(oaiEndpoint) || string.IsNullOrEmpty(oaiKey) || string.IsNullOrEmpty(oaiDeploymentName) )
             {
                 Console.WriteLine("Please check your appsettings.json file for missing or incorrect values.");
                 return;
             }
             
             // Configure the Azure OpenAI client
             OpenAIClient client = new OpenAIClient(new Uri(oaiEndpoint), new AzureKeyCredential(oaiKey));
         
             // Format and send the request to the model
             var chatCompletionsOptions = new ChatCompletionsOptions()
             {
                 Messages =
                 {
                     new ChatRequestSystemMessage(systemMessage),
                     new ChatRequestUserMessage(userMessage)
                 },
                 Temperature = 0.7f,
                 MaxTokens = 800,
                 DeploymentName = oaiDeploymentName
             };
         
         // Get response from Azure OpenAI
         Response<ChatCompletions> response = await client.GetChatCompletionsAsync(chatCompletionsOptions);
             
             ChatCompletions completions = response.Value;
             string completion = completions.Choices[0].Message.Content;
             
             // Write response full response to console, if requested
             if (printFullResponse)
             {
                 Console.WriteLine($"\nFull response: {JsonSerializer.Serialize(completions, new JsonSerializerOptions { WriteIndented = true })}\n\n");
             }
         
             // Write response to console
             Console.WriteLine($"\nResponse:\n{completion}\n\n");
         }      
      ```
   
     **Python**
   
      ```python
   import os
   import asyncio
   from dotenv import load_dotenv
   
   # Add Azure OpenAI package
   from openai import AsyncAzureOpenAI
   
   # Set to True to print the full response from OpenAI for each call
   printFullResponse = False
   
   async def main(): 
           
       try: 
       
           # Get configuration settings 
           load_dotenv()
           azure_oai_endpoint = os.getenv("AZURE_OAI_ENDPOINT")
           azure_oai_key = os.getenv("AZURE_OAI_KEY")
           azure_oai_deployment = os.getenv("AZURE_OAI_DEPLOYMENT")
           
           # Configure the Azure OpenAI client
           client = AsyncAzureOpenAI(
               azure_endpoint = azure_oai_endpoint, 
               api_key=azure_oai_key,  
               api_version="2024-02-15-preview"
               )
   
           while True:
               # Pause the app to allow the user to enter the system prompt
               print("------------------\nPausing the app to allow you to change the system prompt.\nPress anything then enter to continue...")
               input()
   
               # Read in system message and prompt for user message
               system_text = open(file="system.txt", encoding="utf8").read().strip()
               user_text = input("Enter user message: ")
               if user_text.lower() == 'quit' or system_text.lower() == 'quit':
                   print('Exiting program...')
                   break
               
               await call_openai_model(system_message = system_text, 
                                       user_message = user_text, 
                                       model=azure_oai_deployment, 
                                       client=client
                                       )
   
       except Exception as ex:
           print(ex)
   
   async def call_openai_model(system_message, user_message, model, client):
       # Format and send the request to the model
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
   
   
       if printFullResponse:
           print(response)
   
       print("Response:\n" + response.choices[0].message.content + "\n")
   
   if __name__ == '__main__': 
       asyncio.run(main())
      ```

1. To save the changes made to the file, right-click on the file and hit **Save** or press **CTRL+S**.

## Task 5: Run your application

In this task, you will run your configured app to send a request to your model and observe the response. You'll notice that the only difference between the options is the content of the prompt, while all other parameters (such as token count and temperature) remain consistent across requests.

1. In the folder of your preferred language, open `system.txt` in VS Code. For each of the iterations, you'll enter the **System message** in this file and save it. Each iteration will pause first for you to change the system message.

1. In the VS Code terminal, navigate to the folder for your preferred language.

1. If your using as **C#** language kindly open **CSharp.csproj** file replace with following code and save the file with **CTRL+S**.

   ```
   <Project Sdk="Microsoft.NET.Sdk">
   
   <PropertyGroup>
   <OutputType>Exe</OutputType>
   <TargetFramework>net8.0</TargetFramework>
   <ImplicitUsings>enable</ImplicitUsings>
   <Nullable>enable</Nullable>
   </PropertyGroup>
   
    <ItemGroup>
    <PackageReference Include="Azure.AI.OpenAI" Version="1.0.0-beta.14" />
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

1. In the **TERMINAL** pane, make sure you're in the correct folder based on your preferred language.  
    Then, run the application using the appropriate command:

   - **C#:**
     Type `dotnet run` and press **Enter**.

     ![](../media/gg_ex2_1_34.png)

   - **Python:**  
     Type `python prompt-engineering.py` and press **Enter**.

     ![](../media/gg_ex2_1_33.png)

     > **Note:** If you see a message like *"Press any key to continue..."*, press **Enter** to proceed.

1. For the first iteration, enter the following prompts:

    **System message (system.txt)**

    ```prompt
    You are an AI assistant
    ```
     
    ![](../media/system-1upd.png)

    **User message:**

    ```prompt
    Write an intro for a new wildlife Rescue
    ```
   
    ![](../media/x233upd.png)

1. Observe the output. The AI model will likely produce a good generic introduction to a wildlife rescue.

1. Next, enter the following prompts, which specify a format for the response:

    **System message (system.txt)**

    ```prompt
    You are an AI assistant helping to write emails
    ```
    **User message:**

    ```prompt
    Write a promotional email for a new wildlife rescue, including the following: 
       - Rescue name is Contoso 
       - It specializes in elephants 
       - Call for donations to be given at our website
    ```

    > **Note:** You will see a pop-up, click on **Paste as one line**
    
      ![](../media/email1.png)

1. Observe the output. This time, you'll likely see the format of an email with the specific animals included, as well as the call for donations.

1. Next, enter the following prompts that additionally specify the content:

    **System message (system.txt)**

    ```prompt
    You are an AI assistant helping to write emails
    ```

    **User message:**

    ```prompt
    Write a promotional email for a new wildlife rescue, including the following: 
    - Rescue name is Contoso 
    - It specializes in elephants, as well as zebras and giraffes 
    - Call for donations to be given at our website 
    \n Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.
    ```

    > **Note:** You will see a pop-up, click on **Paste as one line**

    ![](../media/email1.png)

1. Observe the output, and see how the email has changed based on your clear instructions.

1. Next, enter the following prompts where we add details about tone to the system message:

    **System message (system.txt)**

    ```prompt
    You are an AI assistant that helps write promotional emails to generate interest in a new business. Your tone is light, chit-chat oriented and you always include at least two jokes.
    ```

    **User message:**

    ```prompt
    Write a promotional email for a new wildlife rescue, including the following: 
    - Rescue name is Contoso 
    - It specializes in elephants, as well as zebras and giraffes 
    - Call for donations to be given at our website 
    \n Include a list of the current animals we have at our rescue after the signature, in the form of a table. These animals include elephants, zebras, gorillas, lizards, and jackrabbits.
    ```
    
    > **Note:** You will see a pop-up, click on **Paste as one line**

1. Observe the output. This time, you'll likely see the email in a similar format, but with a much more informal tone. You'll likely even see jokes included!

1. For the final iteration, we're deviating from email generation and exploring *grounding context*. Here, you provide a simple system message and change the app to provide the grounding context as the beginning of the user prompt. The app will then append the user input, and extract information from the grounding context to answer our user prompt.
15. Open the file `grounding.txt` and briefly read the grounding context you'll be inserting.
16. In your app, immediately after the comment **Format and send the request to the model** and before any existing code, add the following code snippet to read text in from `grounding.txt` to augment the user prompt with the grounding context.

    **C#:** Program.cs

    ```csharp
    // Format and send the request to the model
    Console.WriteLine("\nAdding grounding context from grounding.txt");
    string groundingText = System.IO.File.ReadAllText("grounding.txt");
    userMessage = groundingText + userMessage;
    ```

    **Python:** prompt-engineering.py

    ```python
    # Format and send the request to the model
    print("\nAdding grounding context from grounding.txt")
    grounding_text = open(file="grounding.txt", encoding="utf8").read().strip()
    user_message = grounding_text + user_message
    ```

    > **Note:** Ensure that all indentation errors are corrected before moving forward.

1. Save the file with **CTRL+S** and rerun your app.

1. Enter the following prompts (with the **system message** still being entered and saved in `system.txt`).

    **System message (system.txt)**

    ```prompt
    You're an AI assistant who helps people find information. You'll provide answers from the text provided in the prompt, and respond concisely.
    ```

    **User message:**

    ```prompt
    What animal is the favorite of children at Contoso?
    ```

## Summary

In this lab, you have accomplished the following:
- Provision an Azure OpenAI resource
- Deploy an OpenAI model within the Azure OpenAI Foundry
- Use the functionalities of the Azure OpenAI to generate and improvise code for your production applications.

## You have successfully completed the lab. Click on Next >> to proceed to the next lab.

![Launch Azure Portal](../media/gs_1_7.png)
