# Lab 04: Generate and improve code with Azure OpenAI Service

## Estimated Duration: 60 Minutes

## Lab Overview
In this lab, you will learn how to use Azure OpenAI Service to generate, explain, and improve code using natural language prompts. You will explore code generation in the chat playground and integrate OpenAI into your app to automate code tasks. This will help you enhance productivity by simplifying coding and debugging processes.

The Azure OpenAI Service models can generate code for you using natural language prompts, fixing bugs in completed code, and providing code comments. These models can also explain and simplify existing code to help you understand what it does and how to improve it.

## Lab Objectives
In this lab, you will complete the following tasks:

- Task 1: Provision a Microsoft Foundry resource
- Task 2: Deploy a model
- Task 3: Generate code in the chat playground
- Task 4: Set up an application in Cloud Shell
- Task 5: Configure your application
- Task 6: Run your application

## Task 1: Provision a Microsoft Foundry resource

In this task, you'll create an Azure resource in the Azure portal, selecting the Microsoft Foundry service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **Azure portal**, search for **Microsoft Foundry (1)** and select **Microsoft Foundry (2)** from the results.

   ![](../media/mf-1.png)

1. On the **Microsoft Foundry** overview pane, select **Create a resource**

   ![](../media/mf-2.png)

1. Create an **Foundry** resource using the settings below, then click **Review + create (6)** , leaving all other options at their defaults.
    
    - Subscription: **Default Subscription (1)**
    
    - Resource group: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    
    - Name: **OpenAI-Lab04-<inject key="DeploymentID" enableCopy="false"></inject> (3)**

    - Region: **<inject key="Region" enableCopy="false"></inject> (4)**
    
    - Default project name: **proj-default (5)**
  
      ![](../media/mf-3.png)

1. Under the **Review + create** tab, click on **Create**.

1. Wait for deployment to complete. Click on **Go to resource** to navigate to the deployed foundry resource in the Azure portal.

      ![](../media/mf-4.png)

1. To capture the Keys and Endpoints values, on **OpenAI-Lab04-<inject key="DeploymentID" enableCopy="false"></inject>** blade:

    - On the left navigation menu, expand **Resource Management** and select **Keys and Endpoint (1)**.
    
    - Copy **Key 1 (2)** and ensure to paste it in a text editor such as notepad for future reference.
    
    - Select **OpenAI (3)**, copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as notepad for later use.
    
        ![](../media/mf-5.png "Keys and Endpoints")

<validation step="917cb723-2d65-4411-90f9-0150a7636494" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
- Hit the Validate button for the corresponding task.
- If you receive a success message, you can proceed to the next task.
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

## Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your foundry resource to integrate advanced language capabilities into your applications.

1. In the foundry resource pane, click on **Go to Foundry portal**, which will navigate to **Microsoft Foundry**.

    ![](../media/mf-6.png)
   
1. Click **View deployments** under Use a model.

    ![](../media/SS-1.png)

1. On Deployments tab, click **Deploy (1)**, and choose **Deploy a base model (2)**.

     ![](../media/SS2.png)

1. Search for **gpt-5-mini (1)** in the search bar, select **gpt-5-mini (2)**.

   ![](../media/L1T2S3a-0707.png) 
   
1. On **gpt-5-mini** details page, click on **Custom deploy**.

   ![](../media/L1T2S4-0707.png)

      >**Note:** If the **Custom Deploy** option is not visible, click **Deploy**, then select **Custom settings**.

     ![](../media/mf-7.png) 

1. Within the **Deploy gpt-5-mini** pop-up interface, enter the following details:

      - Deployment name: **my-gpt-model (1)**

      - Deployment type: **Global Standard (2)**

      - Tokens per Minute Rate Limit (thousands): **13K-16k (3)**

      - Guardrails: **DefaultV2 (4)**

      - Click on **Deploy (5)**

         ![](../media/L1T2S5-0707.png)
        
1. This will deploy a model that you will be playing around with as you proceed.

    > **Note:** You can ignore any error related to the assignment of roles to view the quota limits.
   
    > **Note:** Azure OpenAI includes multiple models, each optimized for a different balance of capabilities and performance. In this exercise, you'll use the **gpt-5-mini** model, which is a good model for summarizing and generating natural language and code. For more information about the available models in Azure OpenAI, see [Models](https://learn.microsoft.com/azure/cognitive-services/openai/concepts/models) in the Azure OpenAI documentation.

## Task 3: Generate code in chat playground

In this task, you will examine how Azure OpenAI can generate and explain code in the Chat playground before using it in your app.

1. Once the model is deployed, select **Save as agent**.

     ![](../media/mf-8.png)

    >**Note:** If foundry user role is not assigned, click **Assign me**. Wait for 5 minutes and refresh the page. If **Save as agent** is locked, navigate to agent tab from left navigation and assign from there.

     ![](../media/mf-9.png)

1. On **Create an agent** pop-up, enter the Agent name as **my-gpt-agent (1)** and click **Create and open playground (2)**.

    ![](../media/new-c.png)

1. In the Agent **Playgorund** section, verify that the **my-gpt-model** is selected as Model.

      ![](../media/new-a.png)
   
1. In the **Chat** section, enter the following prompt and press **Enter**.

    ```code
    Write a function in Python that takes a character and a string as input, and returns how many times that character appears in the string
    ```
    
   ![](../media/new/m-1.png)

1. Observe the output. The model will likely respond with a function, with some explanation of what the function does and how to call it.

1. Next, send the prompt:
   ```
   Do the same thing, but this time write it in C#.
   ```

   ![](../media/new/m-2.png)

1. Observe the output. The model likely responded very similarly as the first time, but this time coding in C#. You can ask it again for a different language of your choice, or a function to complete a different task, such as reversing the input string.

1. Next, let's explore using AI to understand code with this example of a random function you saw written in Ruby. Send the following prompt as the user query.

    ```code
    What does the following function do?  
    ---  
    def random_func(n)
      start = [0, 1]
      (n - 2).times do
        start << start[-1] + start[-2]
      end
      start.shuffle.each do |num|
        puts num
      end
    end
    ```

    ![](../media/new/m-3.png)

1. Observe the output, which explains what the function does.

1. Submit the following prompt to get a simpler version of the function.

   ```
   Can you simplify the function?
   ```   

   ![](../media/new/m-4.png)

1. Submit the below-mentioned prompt to add comments to the code.

      ```
      Add some comments to the function.
      ```

      ![](../media/new/m-5.png)

1. Observe the output, which includes comments explaining what each part of the function does. 

## Task 4: Set up an application in Cloud Shell

In this task, you will use a short command-line application running in Cloud Shell on Azure to demonstrate how to integrate with an Azure OpenAI model. Open a new browser tab to access Cloud Shell.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/cloudshell-launch-portal.png#lightbox)      

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**. If you don't see this option, skip the step.  

   ![](../media/new/Bash1.png)

1. If you're prompted as Getting Started, click on **Mount storage account (1)**, select the available subscription **(2)**, and click on **Apply (3)**.

   ![](../media/cloudshell-getting-started.png "Create storage advanced settings")

1. Select **I want to create a storage account (2)** and click on **Next (2)**.

   ![](../media/cloudshell-mount-strg-account.png)

1. Within the **Create storage account** pane, enter the following details:
    - **Subscription**: Default- Choose the only existing subscription assigned for this lab (1).
    - **Resource group**: Select openai-<inject key="Deployment-ID" enableCopy="false"></inject>(2)
    - **CloudShell region**: **<inject key="Region" enableCopy="false"></inject> (3)**
    - **Storage Account Name**: storage<inject key="Deployment-ID" enableCopy="false"></inject>(4)
    - **File share**: Enter **none** (5)
    - Click **Create** (6)

      ![](../media/new/AI17.png)

5. Once the terminal starts, enter the following command to download the sample application and save it to a folder called `mslearn-openai`.

    ```bash
   rm -r mslearn-openai -f
   git clone https://github.com/CloudLabs-MOC/mslearn-openai
    ```

6. The files are downloaded to a folder named **mslearn-openai**. Navigate to the lab files for this task using the following command.

    ```bash
    cd mslearn-openai/Labfiles/04-code-generation
    ```

   > **Note:** Applications for both C# and Python have been provided, as well as sample code we'll be using in this lab.

7. Use the following command to open the lab files in the code editor.

    ```bash
    code .
    ```

   ![](../media/new/AI18.png)

## Task 5: Configure your application

In this task, you will complete key parts of the application to enable it to use your Azure OpenAI resource.

1. In the code editor, expand the language folder for your preferred language.

1. Open the configuration file for your language.

    - **C#:** `appsettings.json`
    - **Python:** `.env`

1. In the configuration file, enter the following values for your Azure OpenAI service:

    - **Endpoint**: The endpoint URL from your Azure OpenAI resource.
    - **Key1**: The primary key from your Azure OpenAI resource.
    - **Deployment Name**: Set this to **my-gpt-model** (the name of your model deployment).
    After updating these values, save the file by right-clicking it in the left pane.

   > **Note:** You can get the Azure OpenAI endpoint and key values from the Azure OpenAI resource's **Key and Endpoint** section under **Resource Management**.

   - **C#:**

      ![](../media/new/AI19.png)

   - **Python:**

      ![](../media/new/AI20.png)

1. Navigate to the folder for your preferred language and install the necessary packages. Enter the below-mentioned command to add the `Azure.AI.OpenAI` package to your project, which is necessary for integrating with Azure OpenAI services.

   For **C#:** 

    ```
    cd CSharp
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.5
    ```
    
    For **Python:**

      ```bash
    cd Python
    pip install --user openai==1.65.2
    ```

1. Open the application code file of your preferred language and update the code. After updating, click **Ctrl+S** to save it.

    - **C#:** `Program.cs`

      ```
      // Implicit using statements are included
      using System.Text;
      using System.Text.Json;
      using Microsoft.Extensions.Configuration;
      using Microsoft.Extensions.Configuration.Json;
      using Azure;
      using Azure.AI.OpenAI;

      // Build a config object and retrieve user settings.
      IConfiguration config = new ConfigurationBuilder()
         .AddJsonFile("appsettings.json")
         .Build();
      string? oaiEndpoint = config["AzureOAIEndpoint"];
      string? oaiKey = config["AzureOAIKey"];
      string? oaiModelName = config["AzureOAIDeploymentName"];

      string command;
      bool printFullResponse = false;

      do
      {
         Console.WriteLine("\n1: Add comments to my function\n" +
            "2: Write unit tests for my function\n" +
            "3: Fix my Go Fish game\n" +
            "\"quit\" to exit the program\n\n" +
            "Enter a number to select a task:");

         command = Console.ReadLine() ?? "";

         switch (command)
         {
            case "1":
                  string functionFile = System.IO.File.ReadAllText("../sample-code/function/function.cs");
                  string commentPrompt = "Add comments to the following function. Return only the commented code.\n---\n" + functionFile;

                  await GetResponseFromOpenAI(commentPrompt);
                  break;
            case "2":
                  functionFile = System.IO.File.ReadAllText("../sample-code/function/function.cs");
                  string unitTestPrompt = "Write four unit tests for the following function.\n---\n" + functionFile;

                  await GetResponseFromOpenAI(unitTestPrompt);
                  break;
            case "3":
                  string goFishFile = System.IO.File.ReadAllText("../sample-code/go-fish/go-fish.cs");
                  string goFishPrompt = "Fix the code below for an app to play Go Fish with the user. Return only the corrected code.\n---\n" + goFishFile;

                  await GetResponseFromOpenAI(goFishPrompt);
                  break;
            case "quit":
                  Console.WriteLine("Exiting program...");
                  break;
            default:
                  Console.WriteLine("Invalid input. Please try again.");
                  break;
         }
      } while (command != "quit");

      async Task GetResponseFromOpenAI(string prompt)
      {
         Console.WriteLine("\nCalling Azure OpenAI to generate code...\n\n");

         if (string.IsNullOrEmpty(oaiEndpoint) || string.IsNullOrEmpty(oaiKey) || string.IsNullOrEmpty(oaiModelName))
         {
            Console.WriteLine("Please check your appsettings.json file for missing or incorrect values.");
            return;
         }

         var credentials = new AzureKeyCredential(oaiKey);
         var chatClient = new OpenAIClient(new Uri(oaiEndpoint), credentials);

         string systemPrompt = "You are a helpful AI assistant that helps programmers write code.";
         string userPrompt = prompt;

         // Temperature and MaxTokens are not set because reasoning models (gpt-5, o-series)
         // reject 'max_tokens' and only support the default temperature.
         var chatOptions = new ChatCompletionsOptions();

         chatOptions.Messages.Add(new ChatMessage(ChatRole.System, systemPrompt));
         chatOptions.Messages.Add(new ChatMessage(ChatRole.User, userPrompt));

         Response<ChatCompletions> completions = await chatClient.GetChatCompletionsAsync(oaiModelName, chatOptions);

         string resultText = completions.Value.Choices[0].Message.Content;

         if (printFullResponse)
         {
            Console.WriteLine($"\nFull response: {JsonSerializer.Serialize(completions.Value, new JsonSerializerOptions { WriteIndented = true })}\n\n");
         }

         Console.WriteLine($"\nResponse:\n{resultText}\n");

         System.IO.File.WriteAllText("result/app.txt", resultText);
         Console.WriteLine($"\nResponse written to result/app.txt\n\n");
      }
      ``` 
    - **Python:** `code-generation.py`
      
      ```
      import os
      from dotenv import load_dotenv

      # Add OpenAI import
      from openai import AzureOpenAI

      # Set to True to print the full response from OpenAI for each call
      printFullResponse = False

      def main():
         try:
            # Get configuration settings
            load_dotenv()
            azure_oai_endpoint = os.getenv("AZURE_OAI_ENDPOINT")
            azure_oai_key = os.getenv("AZURE_OAI_KEY")
            azure_oai_model = os.getenv("AZURE_OAI_DEPLOYMENT")

            # Print environment variables to verify (optional debug)
            print("Endpoint:", azure_oai_endpoint)
            print("Key:", azure_oai_key[:5] + "..." + azure_oai_key[-5:])  # Masked display
            print("Deployment:", azure_oai_model)

            # Set OpenAI configuration settings
            global client
            client = AzureOpenAI(
                  api_key=azure_oai_key,
                  azure_endpoint=azure_oai_endpoint,
                  api_version="2025-04-01-preview"  # Reasoning models (gpt-5, o-series) need 2024-12-01-preview or later
            )

            # Ensure 'result' folder exists
            os.makedirs("result", exist_ok=True)

            while True:
                  print('\n1: Add comments to my function\n' +
                     '2: Write unit tests for my function\n' +
                     '3: Fix my Go Fish game\n' +
                     '\"quit\" to exit the program\n')
                  command = input('Enter a number to select a task:')
                  if command == '1':
                     file = open(file="../sample-code/function/function.py", encoding="utf8").read()
                     prompt = "Add comments to the following function. Return only the commented code.\n---\n" + file
                     call_openai_model(prompt, model=azure_oai_model)
                  elif command == '2':
                     file = open(file="../sample-code/function/function.py", encoding="utf8").read()
                     prompt = "Write four unit tests for the following function.\n---\n" + file
                     call_openai_model(prompt, model=azure_oai_model)
                  elif command == '3':
                     file = open(file="../sample-code/go-fish/go-fish.py", encoding="utf8").read()
                     prompt = "Fix the code below for an app to play Go Fish with the user. Return only the corrected code.\n---\n" + file
                     call_openai_model(prompt, model=azure_oai_model)
                  elif command.lower() == 'quit':
                     print('Exiting program...')
                     break
                  else:
                     print("Invalid input. Please try again.")

         except Exception as ex:
            print(ex)

      def call_openai_model(prompt, model):
         # Provide a basic user message, and use the prompt content as the user message
         system_message = "You are a helpful AI assistant that helps programmers write code."
         user_message = prompt

         # Build the messages array
         messages = [
            {"role": "system", "content": system_message},
            {"role": "user", "content": user_message},
         ]

         # Call the Azure OpenAI model
         # temperature and max_tokens are not set because reasoning models (gpt-5, o-series)
         # reject 'max_tokens' and only support the default temperature.
         response = client.chat.completions.create(
            model=model,  # Use the model parameter passed
            messages=messages
         )

         # Extract response content
         output = response.choices[0].message.content

         # Print the response to the console
         print("\n--- Response Start ---\n")
         print(output)
         print("\n--- Response End ---\n")

         # Write the response to a file
         with open("result/app.txt", "w", encoding="utf8") as results_file:
            results_file.write(output)

         print("Response written to result/app.txt\n")

      if __name__ == '__main__':
         main()
      ```
      
## Task 6: Run your application

In this task, you will run your configured app to generate code for each use case, which is numbered in the app and can be executed in any order.

> **Note:** Some users may experience rate limiting if calling the model too frequently. If you hit an error about a token rate limit, wait for a minute then try again.

1. In the code editor, expand the `sample-code` folder and briefly observe the function and the app for your language. The OpenAI tool will use these files to generate the responses. 
   
   ![](../media/new/AI21.png)

1. In the Cloud Shell bash terminal, navigate to the folder for your preferred language.

1. Run the application.

    - **C#:** `dotnet run`
    - **Python:** `python code-generation.py`

      >**Note:** If you encounter any errors after running the Python script, try upgrading the OpenAI package by running the following command: `pip install --user --upgrade openai`

      >**Note:** If you encounte error  `No module named 'dotenv'`, run this `pip install --user python-dotenv openai`.

1. Choose option **1** to add comments to your code. Note, the response might take a few seconds for each of these tasks.

   ![](../media/new/AI22.png)

1. In the response, you will see that OpenAI has added comments to your sample code provided from the function file. 

1. Next, choose option **2** to write unit tests for that same function.

   ![](../media/new/AI23.png)

1. In the response, you will notice that the unit tests are added to your sample code.

1. Next, choose option **3** to fix bugs in an app for playing Go Fish. 

   ![](../media/new/AI24.png)

1. This time, OpenAI would use the go fish file and fix the code in it and respond with the updated code. 

1. The results will replace what was in `result/app.txt`, and should have very similar code with a few things corrected.

    - **C#:** Fixes are made on lines 30 and 59
    - **Python:** Fixes are made on lines 18 and 31

        >**Note:** Click on Ctrl+C to stop the project.

10. To check the results, paste the following code in the terminal:

    ```
    cd result
    ```

11. Copy the below command in the terminal to see the contents of the app.txt file.

     ```
     cat app.txt
     ```

      ![](../media/new/AI25.png)

The app for Go Fish in `sample-code` can be run if you replace the lines with bugs with the response from Azure OpenAI. If you run it without the fixes, it will not work correctly.

It's important to note that even though the code for this Go Fish app was corrected for some syntax, it's not a strictly accurate representation of the game. If you look closely, there are issues with not checking if the deck is empty when drawing cards, not removing pairs from the player's hand when they get a pair, and a few other bugs that require an understanding of card games to realize. This is a great example of how useful generative AI models can be to assist with code generation, but they can't be trusted as correct and need to be verified by the developer.

If you would like to see the full response from Azure OpenAI, you can set the `printFullResponse` variable to `True` and re-run the app.

## Summary

In this lab, you explored how to use Azure OpenAI Service to generate, explain, and improve code using natural language prompts. You generated code in different programming languages, explained existing code, and simplified functions using the chat playground. You also set up a command-line application in Cloud Shell, configured it to use your Azure OpenAI resource, and ran the application to automate code tasks such as adding comments, writing unit tests, and fixing bugs.

### You have successfully completed the lab. Click on **Next >>** to proceed with the next lab.
     
![](../media/new/next.png)
