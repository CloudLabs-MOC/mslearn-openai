# Lab 04: Generate and improve code with Azure OpenAI Service

## Lab scenario
The Azure OpenAI Service models can generate code for you using natural language prompts, fixing bugs in completed code, and providing code comments. These models can also explain and simplify existing code to help you understand what it does and how to improve it.

## Lab objectives
In this lab, you will perform:
- Provision an Azure OpenAI resource
- Deploy an OpenAI model within the Azure OpenAI studio
- use the functionalites of the Azure OpenAI to generate and improvise code for your production applications

## Estimated time: 30 minutes

## Architecture Diagram

  ![](media/lab-04-ad.PNG "Architecture Diagram")
  
## Task 1: Provision an Azure OpenAI resource

Before you can use Azure OpenAI models, you must provision an Azure OpenAI resource in your Azure subscription.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/openai8.png)

2. On **Cognitive Services | Azure OpenAI** blade, click on **Create**.

   ![](../media/openai_create.png)

3. create an **Azure OpenAI** resource with the following settings:

    - **Subscription**: Default - Pre-assigned subscription.
    - **Resource group**: openai-<inject key="Deployment-id" enableCopy="false"></inject>
    - **Region**: Default - Make sure that the default region selected is either East US or West Europe. 
    - **Name**: OpenAI-Lab04-<inject key="Deployment-id" enableCopy="false"></inject>
    - **Pricing tier**: Standard S0
  
   ![](../media/openai-lab01_01.png "Create Azure OpenAI resource")
    
4. Wait for deployment to complete. Then go to the deployed Azure OpenAI resource in the Azure portal.
5. On **openai-<inject key="DeploymentID" enableCopy="false"/>** blade, select **Keys and Endpoint (1)** under **Resource Management**. Copy **Key 1 (2)** and the **Endpoint (3)** by clicking on copy to clipboard paste it in a text editor such as notepad for later use.

   ![](../media/openai-labs_keys&endpoints.png "Keys and Endpoints")

  **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:

  > - Navigate to the Lab Validation tab, from the upper right corner in the lab guide section.
  > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
  > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
  > - If you need any assistance, please contact us at labs-support@spektrasystems.com.

## Task 2: Deploy a model

To use the Azure OpenAI API for code generation, you must first deploy a model to use through the **Azure OpenAI Studio**. Once deployed, we will use the model with the playground and reference that model in our app.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/openai8.png)

2. On **Cognitive Services | Azure OpenAI** blade, select **OpenAI-Lab04-<inject key="Deployment-id" enableCopy="false"></inject>**

   ![](../media/OpenAI_select.png)

3. In the Azure OpenAI resource pane, click on **Go to Azure OpenAI Studio** it will navaigate to **Azure AI Studio**.

   ![](../media/openai_studio.png)
   
4. In **Welcome to Azure OpenAI Service** page, click on **Create new deployment**.

   ![](../media/openai-lab01_t2_s2.png "Create a new deployment")

5. In the **Deployments** page, click on **+ Create new deployment**.

   ![](../media/openai-lab01_t2_s3.png "Create a new deployment")

6. Within the **Deploy model** pop-up interface, enter the following details and then click on **Advanced options (3)** followed by scaling down the **Tokens per Minute Rate Limit (thousands) (4)**:
    - **Select a model**: gpt-35-turbo
    - **Model version**: *Use the default version*
    - **Deployment name**: 35turbo
    - **Tokens per Minute Rate Limit (thousands)**: 10K
  
   ![](../media/openai-labs_deploy-model-4.png "Deploy model configurations")

7. Click on the **Create** button to deploy a model which you will be playing around with as you proceed.

> **Note**: Each Azure OpenAI model is optimized for a different balance of capabilities and performance. We'll use the **3.5 Turbo** model series in the **GPT-3** model family in this exercise, which is highly capable for both language and code understanding.

  **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:

  > - Navigate to the Lab Validation tab, from the upper right corner in the lab guide section.
  > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
  > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
  > - If you need any assistance, please contact us at labs-support@spektrasystems.com.

## Task 3: Generate code in chat playground

Before using in your app, examine how Azure OpenAI can generate and explain code in the chat playground.

1. In [Azure OpenAI Studio](https://oai.azure.com/?azure-portal=true), navigate to the **Chat** playground in the left pane.
1. In the **Assistant setup** section at the top, select the **Default** system message template.
1. In the **Chat session** section, enter the following prompt and press *Enter*.

    ```code
   Write a function in python that takes a character and string as input, and returns how many times that character appears in the string
    ```

1. The model will likely respond with a function, with some explanation of what the function does and how to call it.
1. Next, send the prompt `Do the same thing, but this time write it in C#`.
1. Observe the output. The model likely responded very similarly as the first time, but this time coding in C#. You can ask it again for a different language of your choice, or a function to complete a different task such as reversing the input string.
1. Next, let's explore using AI to understand code with this example of a random function you saw written in Ruby. Send the following prompt as the user message.

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

1. Observe the output, which explains what the function does in natural language. Try asking the model to rewrite it in a language you are familiar with.

## Task 4: Set up an application in Cloud Shell

To show how to integrate with an Azure OpenAI model, we'll use a short command-line application that runs in Cloud Shell on Azure. Open up a new browser tab to work with Cloud Shell.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/cloudshell-launch-portal.png#lightbox)

2. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**. If you don't see this option, skip the step.  

3. If you're prompted to create storage for your Cloud Shell, ensure your subscription is specified and then select **Advanced settings**.

   ![](../media/openai-labs_createstoragepane.png "Create storage advanced settings")

4. Within the **Advanced settings** pane, enter the following details and then click on **Create storage**:
    - **Subscription**: Default- Choose the only existing subscription assigned for this lab.
    - **CloudShell region**: East US
    - **Resource group**: Select **Use existing**.
      - openai-<inject key="Deployment-id" enableCopy="false"></inject>
    - **Storage account**: Select **Create new**.
      - storage<inject key="Deployment-id" enableCopy="false"></inject>
    - **File share**: Create a new file share named **none**

   ![](../media/openai-labs_advancedsettings_config.png "Create storage advanced settings")

5. Make sure the type of shell indicated on the top left of the Cloud Shell pane is switched to *Bash*. If it's *PowerShell*, switch to *Bash* by using the drop-down menu.

6. Once the terminal starts, enter the following command to download the sample application and save it to a folder called `azure-openai`.

    ```bash
   rm -r azure-openai -f
   git clone https://github.com/MicrosoftLearning/mslearn-openai azure-openai
    ```

7. The files are downloaded to a folder named **azure-openai**. Navigate to the lab files for this exercise using the following command.

    ```bash
   cd azure-openai/Labfiles/04-code-generation
    ```

    Applications for both C# and Python have been provided, as well as sample code we'll be using in this lab.

    Open the built-in code editor, and you can observe the code files we'll be using in `sample-code`. Use the following command to open the lab files in the code editor.

    ```bash
   code .
    ```

  **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:

  > - Navigate to the Lab Validation tab, from the upper right corner in the lab guide section.
  > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
  > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
  > - If you need any assistance, please contact us at labs-support@spektrasystems.com.

## Task 5: Configure your application

For this exercise, you'll complete some key parts of the application to enable using your Azure OpenAI resource.

1. In the code editor, expand the language folder for your preferred language.

2. Open the configuration file for your language.

    - **C#**: `appsettings.json`
    - **Python**: `.env`

3. Update the configuration values to include the **endpoint** and **key** from the Azure OpenAI resource you created, as well as the name of your deployment, `35turbo`. Then save the file by using the shortcut keys CTRL+S or CMD+S.

4. Navigate to the folder for your preferred language and install the necessary packages.

    **C#**

    ```bash
   cd CSharp
   dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.5
    ```

    **Python**

    ```bash
   cd Python
   pip install python-dotenv
   pip install openai
    ```

5. Select the code file in this folder for your language and add the necessary libraries.

    **C#**

    `Program.cs`

    ```csharp
   // Add Azure OpenAI package
   using Azure.AI.OpenAI;
    ```

    **Python**

    `code-generation.py`

    ```python
   # Add OpenAI import
   import openai
    ```

6. Add the necessary code for configuring the client.

    **C#**

    ```csharp
   // Initialize the Azure OpenAI client
   OpenAIClient client = new OpenAIClient(new Uri(oaiEndpoint), new AzureKeyCredential(oaiKey));
    ```

    **Python**

    ```python
   # Set OpenAI configuration settings
   openai.api_type = "azure"
   openai.api_base = azure_oai_endpoint
   openai.api_version = "2023-05-15"
   openai.api_key = azure_oai_key
    ```

7. In the function that calls the Azure OpenAI model, add the code to format and send the request to the model.

    **C#**

    ```csharp
    // Create chat completion options
    var chatCompletionsOptions = new ChatCompletionsOptions()
    {
        Messages =
        {
            new ChatMessage(ChatRole.System, systemPrompt),
            new ChatMessage(ChatRole.User, userPrompt)
        },
        Temperature = 0.7f,
        MaxTokens = 1000,
    };

    // Get response from Azure OpenAI
    Response<ChatCompletions> response = await client.GetChatCompletionsAsync(
        oaiModelName,
        chatCompletionsOptions
    );

    ChatCompletions completions = response.Value;
    string completion = completions.Choices[0].Message.Content;
    ```

    **Python**

    ```python
   # Build the messages array
   messages =[
       {"role": "system", "content": system_message},
       {"role": "user", "content": user_message},
   ]

   # Call the Azure OpenAI model
   response = openai.ChatCompletion.create(
       engine=model,
       messages=messages,
       temperature=0.7,
       max_tokens=1000
   )
    ```

8. To save the changes made to the file, execute CTRL+S or CMD+S.

## Task 6: Run your application

Now that your app has been configured, run it to try generating code for each use case. The use case is numbered in the app, and can be run in any order.

> **Note**: Some users may experience rate limiting if calling the model too frequently. If you hit an error about a token rate limit, wait for a minute then try again.

1. In the code editor, expand the `sample-code` folder and briefly observe the function and the app for your language. These files will be used for the tasks in the app.
1. In the Cloud Shell bash terminal, navigate to the folder for your preferred language.
1. Run the application.

    - **C#**: `dotnet run`
    - **Python**: `python code-generation.py`

1. Choose option **1** to add comments to your code. Note, the response might take a few seconds for each of these tasks.
1. The results will be put into `result/app.txt`. Open that file up, and compare it to the function file in `sample-code`.
1. Next, choose option **2** to write unit tests for that same function.
1. The results will replace what was in `result/app.txt`, and details four unit tests for that function.
1. Next, choose option **3** to fix bugs in an app for playing Go Fish.
1. The results will replace what was in `result/app.txt`, and should have very similar code with a few things corrected.

    - **C#**: Fixes are made on line 30 and 59
    - **Python**: Fixes are made on line 18 and 31

The app for Go Fish in `sample-code` can be run, if you replace the lines with bugs with the response from Azure OpenAI. If you run it without the fixes, it will not work correctly.

It's important to note that even though the code for this Go Fish app was corrected for some syntax, it's not a strictly accurate representation of the game. If you look closely, there are issues with not checking if the deck is empty when drawing cards, not removing pairs from the players hand when they get a pair, and a few other bugs that require understanding of card games to realize. This is a great example of how useful generative AI models can be to assist with code generation, but can't be trusted as correct and need to be verified by the developer.

If you would like to see the full response from Azure OpenAI, you can set the `printFullResponse` variable to `True`, and rerun the app.

## Review

In this lab, you have accomplished the following:
-   Provision an Azure OpenAI resource
-   Deploy an OpenAI model within the Azure OpenAI studio
-   Use the functionalites of the Azure OpenAI to generate and improvise code for your production applications.

### You have successfully completed the lab
