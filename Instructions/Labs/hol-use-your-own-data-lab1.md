# Lab 01: Use your own data with Azure OpenAI

### Estimated Duration: 120 Minutes

## Lab Overview

In this lab, you will learn how to integrate your own data with the Azure OpenAI Service to build grounded AI solutions. You will provision the Azure OpenAI resource, deploy a model, and connect it to your custom data source. Finally, you will configure and run an application to observe how the model generates responses using your specific data. The Azure OpenAI Service enables you to use your own data with the intelligence of the underlying LLM. You can limit the model to only use your data for pertinent topics, or blend it with results from the pre-trained model.

## Lab Objectives
In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Observe normal chat behavior without adding your own data
- Task 4: Connect your data in the chat playground
- Task 5: Chat with a model grounded in your data
- Task 6: Set up an application in Cloud Shell
- Task 7: Configure your application
- Task 8: Run your application

## Task 1: Provision an Azure OpenAI resource

Before you can use Azure OpenAI models, you must provision an Azure OpenAI resource in your Azure subscription.

1. In the **Azure portal**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)**.

   ![](../media/search.png)

2. On **Microsoft Foundry | Azure OpenAI (1)** blade, click on **Create (2)**, click on **Azure OpenAI (3)**.

   ![](../media/L1T1S2.png)

3. Create an **Azure OpenAI** resource with the following settings and then click on **Next (6)** thrice.
   
    - Subscription: **Default - Pre-assigned subscription (1)**.
    - Resource group: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    - Region: Select **East US 2 (3)**
    - Name: **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> (4)**
    - Pricing tier: **Standard S0 (5)**
  
      ![](../media/L1T1S3-2107.png "Create Azure OpenAI resource")
    
4. Click on **Create**.

5. Wait for deployment to complete. Then click on **Go to resource group**.

   ![](../media/L1T1S5-2107.png)

6. To capture the Keys and Endpoints values, on **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject>** blade:
   
      - Select **Keys and Endpoint (1)** under **Resource Management**.
      - Click on **Show Keys (2)**.
      - Copy **Key 1 (3)** and ensure to paste it in a text editor such as Notepad for future reference.
      - Finally, copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as Notepad for later use.

      ![](../media/L1T1S6-2107.png "Keys and Endpoints")


   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:    
   - If you receive a success message, you can proceed to the next task.
   - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

   <validation step="8b72507c-7e1f-49a4-b1a7-68ce5f2e3aee" />

## Task 2: Deploy a model

To chat with the Azure OpenAI, you must first deploy a model to use through the **Azure AI Foundry portal**. Once deployed, we will use the model with the playground and use our data to ground its responses.

1. In the **Azure portal**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)**.

      ![](../media/search.png)

1. On **AI Foundry | Azure OpenAI (1)** blade, select **OpenAI-Lab01-<inject key="DeploymentID" enableCopy="false"></inject> (2)**.

      ![](../media/L1T2S2-2107.png)

1. In the Azure OpenAI resource pane, **Overview (1)** section, click on **Go to Azure AI Foundry portal (2)** it will navigate to **Azure AI Foundry portal**.

      ![](../media/L1T2S3-2107.png)

1. After navigating to Azure AI Foundry portal, if prompted, click on **Close** pop-up on the top.

1. Click on Azure AI Foundry portal, go to **Deployments (1)** from the left navigation pane, click on **+ Deploy model (2)**, select **Deploy base Model (3)**.  

   ![](../media/L1T2S5-2107.png)

1. In the **Select a model** window, select **gpt-4o-mini (1)** and click on **Confirm (2)**.

   ![](../media/L1T2S6.png)

1. Click on **Customize**.

   ![](../media/L1T2S7.png)

1. Within the **Deploy model** pop-up interface, enter the following details:
    
    - **Deployment name**: **text-turbo (1)**
    - **Deployment type**: **Standard (2)**
    - **Model version**: **2024-07-18 (Default) (3)** ( Check the Deployment name after changing the model version. If it is changed, please update it to **text-turbo**)
    - Click on customize to reduce **Tokens per Minute Rate Limit**: **20K (4)**
    - Click on **Deploy (5)**
  
   ![](../media/L1T2S8.png)

1. This will deploy a model that you will be playing around with as you proceed.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:      
- If you receive a success message, you can proceed to the next task.
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
     
<validation step="b04e38bd-81d8-4651-882b-bb5b0139fee8" />


## Task 3: Observe normal chat behavior without adding your own data

Before connecting Azure OpenAI to your data, first observe how the base model responds to queries without any grounding data.

1. In the Azure AI Foundry portal, from the **Playground** section, select the **Chat** page. 

   ![](../media/L1T3S1-2107.png)

2. The **Chat** playground page consists of three main sections:

    - **Setup** - used to set the context for the model's responses.
    - **Chat session** - used to submit chat messages and view responses.
    - **Configuration** - used to configure settings for the model deployment.

3. In the **Setup** area, ensure that your model deployment **`text-turbo(version:2024-07-18 (Default))`(1)** is selected. Select the Default system message to set the context for the chat session. The default system message is **`You are an AI assistant that helps people find information`(2)**.

      ![](../media/L1T3S3.png)
   
      >**Note:** On the **Update system message?** pop-up, select **Continue**.

6. In the **Chat session**, submit the following queries **(1)**, click the send button **(2)** and review the responses:

      ```
      I'd like to take a trip to New York. Where should I stay?
      ```

      ```
      What are some facts about New York?
      ```

      ![](../media/L1T3S5.1-2107.png)   

      ![](../media/L1T3S5.2-2107.png)   

      >**Note:** Try similar questions about tourism and places to stay for other locations that will be included in our grounding data, such as London, or San Francisco. You'll likely get complete responses about areas or neighborhoods, and some general facts about the city.


## Task 4: Connect your data in the chat playground

In this task ,you will add your data in the chat playground to see how it responds with your data as grounding

1. In the **Azure portal**, search for **Storage Account** and select **Storage Account**.

      ![](../media/L1T4S1-2107.png)

1. On **Storage Account** page, click on **+ Create**.

      ![](../media/L1T4S2.png)

1. Create a **Storage Account** resource with the following settings:

    - Subscription: **Default - Pre-assigned subscription (1)**
    - Resource group: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    - Storage account name: **storage<inject key="DeploymentID" enableCopy="false"></inject> (3)**
    - Region: Select **<inject key="Region" enableCopy="false" /> (4)**
    - Redundancy: **Locally-redundant storage (LRS) (5)**

    - Select **Next (6)**
  
         ![](../media/L1T4S3-2107.png "Create storage account")

    - **Allow enable anonymous access on individual containers**: check in the box to enable under advance section **(1)**. Click on **Review + Create (2)**.  

         ![](../media/L1T4S3.2-2107.png "allow blob access")

1. Click on **Create**         

1. Wait until the storage account is created before you proceed to the next task. This should take about a minute.

1. On the deployment blade, click **Go to resource**.

1. On the **Storage Account** page, from the left navigation, select **Containers (1)** under Data storage and click on **+ Add container (2)**.

      ![](../media/L1T4S7-2107.png "upload files")

1. Create a container with the name **openaidatasource (1)**, and under **Anonymous access level** select **Container (2)**. Select **Create (3)**.

      ![](../media/L1T4S8-2107.png "create container")

1. Select the **openaidatasource** container, and select **Upload**.

      ![](../media/L1T4S9-2107.png)

1. Click on **Browse for files**.

      ![](../media/L1T4S10-2107.png)

1. Navigate to `C:\AllFiles\mslearn-openai-main\Labfiles\06-use-own-data\data`, press **Enter** **(1)**. Select all the files that you have extracted **(2)** and then click on **Open (3)**.

      ![](../media/L1T4S11-2107.png "upload files")

1. Click on **Upload**.

      ![](../media/L1T4S12-2107.png)

1. In the **Azure portal**, search for **AI search (1)** and select **AI search (2)**.

      ![](../media/u22.png)

2.  On **Microsoft Foundry | AI search (1)** blade, click on **Create (2)**.

      ![](../media/L1T4S14.png "upload files")

3. Create an **AI Search** resource with the following settings and click on **Review + create (6)**. 

    - Subscription: **Default - Pre-assigned subscription (1)**
    - Resource group: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    - Service name: **cognitive-search-<inject key="DeploymentID" enableCopy="false"></inject> (3)**
    - Location: Select **<inject key="Region" enableCopy="false" /> (4)**
    - Pricing tier: **Basic (5)** (Click on **Change Pricing Tier**, click on **Basic** and then click **Select**).

      ![](../media/L1T4S15-2107.png "Create cognitive search resource")

1. Click on **Create**.      

1. Wait until your search resource has been deployed. Select **Go to resources**.

1. Navigate to the **cognitive-search-<inject key="DeploymentID" enableCopy="false"></inject>** and in the overview page **copy the URL and paste it in a text editor such as notepad for later use.**

      ![](../media/L1T4S18-2107.png)

1. From the left navigation pane, under **Settings**, click on **Keys (1)** and copy the **primary key (2)** or secondary key and paste it in a notepad file for later use.

      ![](../media/L1T4S19-2107.png)

1. Navigate to the **Chat (1)** playground followed by select **Add your data(2)** in the setup pane and click on **+ Add a data source (3)**.

      ![](../media/add_data1.png "Add your data in setup pane")
   
1. In the **Add data**, enter the following values for your data source and then click on **Next**.

    - Select data source: **Azure Blob Storage (1)**
    - Select Azure Blob storage resource: **Choose the storage resource you created (2)**
    - Select storage container: **Choose the storage container you created (3)**
    - Select Azure AI Search resource: **Choose the search resource you created (4)**
    - Enter the index name: **margiestravel (5)**
    - Indexer schedule: **Once (6)**
    - Click on **Next (7)** 

      
      ![](../media/L1T4S21-new.png "Add data configurations")
   
  1. On the **Data management** page select the **1024(default)** search type from the drop-down, and then select **Next**.

      ![](../media/data_management-1.png "Add data")

1. On the **Data Connection** page, select **API key** and then click **Next**.
   
      ![](../media/api_key.png "Add data")
   
1. On the **Review and finish** page select **Save and close**, which will add your data. This may take a few minutes, during which you need to leave your window open. 
   
      ![](../media/L1T4S24-2107.png "Add data")

1. Once completed, verify if the data source, **search resource**, and index specified **margiestravel** is present under the **Add your data** tab in **Assistant setup** pane.

      ![](../media/L1T4S25-2107.png)
   
> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:      
- If you receive a success message, you can proceed to the next task.
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
  
<validation step="f6630936-2440-4068-8b5e-3d93f1443da0" />


## Task 5: Chat with a model grounded in your data

1. Now that you've added your data, ask the same questions as you did previously, and see how the response differs.

   ```
   I'd like to take a trip to New York. Where should I stay?
   ```

   ```
   What are some facts about New York?
   ```

      >**Note:** You'll notice a very different response this time, with specifics about certain hotels and a mention of Margie's Travel, as well as references to where the information provided came from. If you open the PDF reference listed in the response, you'll see the same hotels as the model provided.
      
      >**Note:** If you encounter any errors, try refreshing the browser and repeating the process from step 1.

1. Try asking it about other cities included in the grounding data, which are Dubai, Las Vegas, London, and San Francisco.

      >**Note**: **Add your data** is still in preview and might not always behave as expected for this feature, such as giving the incorrect reference for a city not included in the grounding data.

## Task 6: Set up an application in Cloud Shell

To show how to integrate with an Azure OpenAI model, we'll use a short command-line application that runs in Cloud Shell on Azure. Open up a new browser tab to work with Cloud Shell.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

      ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/cloudshell-launch-portal.png)

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**.

1. Within the Getting Started pane, select **Mount storage account**, select your **Storage account subscription** from the dropdown and click **Apply**.

      ![](../media/cloudshell-getting-started.png)

1. Within the **Mount storage account** pane, select **I want to create a storage account** and click **Next**.

      ![](../media/cloudshell-mount-strg-account.png)

1. Within the **Create Storage account** pane, enter the following details:
    - Subscription: **Default- Choose the only existing subscription assigned for this lab (1)**.
    - Resource group: Select **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**    
    - CloudShell region: **East US (3)**
    - **Storage account**: **str<inject key="DeploymentID" enableCopy="false"></inject> (4)**
    - **File share**: Enter **none (5)**
    - Click **Create (6)**

      ![](../media/u28.png "Create storage advanced settings")

1. Once the terminal opens, click on **Settings (1)** and select **Go to Classic version (2)**.

   ![](../media/classic-cloudshell.png)

1. Enter the following command to download the sample application and save it to a folder called `mslearn-openai`.

    ```bash
   rm -r mslearn-openai -f
   git clone https://github.com/microsoftlearning/mslearn-openai mslearn-openai
    ```

    ![](../media/u30.png "Create storage advanced settings")

1. The files are downloaded to a folder named **mslearn-openai**. You can just navigate to the lab files for this exercise using the following command.

    ```bash
   cd mslearn-openai/Labfiles/02-use-own-data
    ```

    Applications for both C# and Python have been provided, as well as sample code we'll be using in this lab.

1. Open the built-in code editor, and you can observe the code files we'll be using in `sample-code`. Use the following command to open the lab files in the code editor.

    ```bash
   code .
    ```  
   
## Task 7: Configure your application

For this exercise, you'll complete some key parts of the application to enable using your Azure OpenAI resource.

1. In the code editor, expand the language folder for your preferred language.

1. Open the configuration file for your preferred language

    - **C#**: appsettings.json
    - **Python**: .env

1. Update the configuration values to include:
    - The  **endpoint** and a **key** from the Azure OpenAI resource you created (Which you copied in the previous task). Alternatively, it is available on the **Keys and Endpoint** page for your Azure OpenAI resource in the Azure portal.
    
    - The **deployment name** you specified for your model deployment (available in the **Deployments** page in Azure AI Foundry portal that is **text-turbo**).
    
    - The endpoint for your AI search service (Which you copied in the previous task; alternatively, it is available in the **Url** value on the overview page for your AI search resource in the Azure portal).
    
    - A **key** for your search resource (available in the **Keys** page for your AI search resource in the Azure portal - you can use either of the admin keys)
    - The name of the search index (which should be `margiestravel`).

    - Press **Ctrl + S** on your keyboard to save the file.

      ![](../media/app-set-2107.png)

      ![](../media/env-file-2107.png)

1. If you're using **C#**, navigate to `CSharp.csproj`, delete the existing code, then replace it with the following code and then press **Ctrl+S** to save the file.

    ```
    <Project Sdk="Microsoft.NET.Sdk">
     
       <PropertyGroup>
         <OutputType>Exe</OutputType>
         <TargetFramework>net8.0</TargetFramework>
         <ImplicitUsings>enable</ImplicitUsings>
         <Nullable>enable</Nullable>
         <LangVersion>12</LangVersion>
       </PropertyGroup>
     
       <ItemGroup>
         <PackageReference Include="Azure.AI.OpenAI" Version="2.1.0" />
         <PackageReference Include="Azure.Search.Documents" Version="11.6.0" />
         <PackageReference Include="Microsoft.Extensions.Configuration" Version="8.0.0" />
         <PackageReference Include="Microsoft.Extensions.Configuration.Json" Version="8.0.0" />
         <PackageReference Include="Newtonsoft.Json" Version="13.0.3" />
       </ItemGroup>
     
       <ItemGroup>
         <None Update="appsettings.json">
           <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
         </None>
       </ItemGroup>
     
     </Project>
    ```   

1. Navigate to the folder for your preferred language and install the necessary packages.

     **C#**:

    ```
    cd CSharp
    export DOTNET_ROOT=$HOME/.dotnet
    export PATH=$DOTNET_ROOT:$PATH
    mkdir -p $DOTNET_ROOT
    ```     

     >**Note**: Azure Cloud Shell often does not have admin privileges, so you need to install .NET in your home directory. So here Your creating a separate `.dotnet` directory under your home directory to isolate your configuration.
     - `DOTNET_ROOT` specifies where your .NET runtime and SDK are located (in your `$HOME/.dotnet directory`).
     - `PATH=$DOTNET_ROOT:$PATH` ensures that the locally installed .NET SDK can be accessed globally by your terminal.
     - `mkdir -p $DOTNET_ROOT` This creates the directory where the .NET runtime and SDK will be installed.

1.  Run the following command to install the required SDK version locally:     

     ```
     wget https://dotnet.microsoft.com/download/dotnet/scripts/v1/dotnet-install.sh
     chmod +x dotnet-install.sh
     ./dotnet-install.sh --version 8.0.404 --install-dir $DOTNET_ROOT
     ```

      >**Note**: These commands download and prepare the official `.NET` installation script, grant it execute permissions, and install the required .NET SDK version (8.0.404) in the `$DOTNET_ROOT` directory as we dont have the admin privileges to install it globally.

1. Enter the following command to restore the workload.

    ```
    dotnet workload restore
    ```

     >**Note**: Restores any required workloads for your project, such as additional tools or libraries that are part of the .NET SDK.
    
1. Enter the following command to add the `Azure.AI.OpenAI` NuGet package to your project, which is necessary for integrating with AI Foundry.

    ```
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.14
    ```

1. If you are using Python, navigate to the **Python** folder and install the necessary packages.

    **Python**:

    ```
    cd Python
    pip install python-dotenv
    pip install openai==1.56.2
    pip install openai requests python-dotenv
    ```
      > **Note:** If you receive a permission error after executing the installation command as shown in the image, please run the command below for installation.
      >    ![](../media/L2T3S9python-0205.png)
      > ```bash
      > pip install --user python-dotenv
      > pip install --user openai==1.56.2
      > pip install --user openai requests python-dotenv
      > ```

1. Open the code file for your preferred language, and replace the comment ***Configure your data source*** with code to add the Azure OpenAI SDK library:

    **C#**: OwnData.cs

    ```csharp
    // Configure your data source
     // Extension methods to use data sources with options are subject to SDK surface changes. Suppress the warning to acknowledge this and use the subject-to-change AddDataSource method.
     #pragma warning disable AOAI001
     
     ChatCompletionOptions chatCompletionsOptions = new ChatCompletionOptions()
     {
        MaxOutputTokenCount = 600,
        Temperature = 0.9f,
     };
     
     chatCompletionsOptions.AddDataSource(new AzureSearchChatDataSource()
     {
        Endpoint = new Uri(azureSearchEndpoint),
        IndexName = azureSearchIndex,
        Authentication = DataSourceAuthentication.FromApiKey(azureSearchKey),
     });
    ```
    
    **Python**: ownData.py

    ```python
    # Configure your data source
     text = input('\nEnter a question:\n')
     
     completion = client.chat.completions.create(
        model=deployment,
        messages=[
            {
                "role": "user",
                "content": text,
            },
        ],
        extra_body={
            "data_sources":[
                {
                    "type": "azure_search",
                    "parameters": {
                        "endpoint": os.environ["AZURE_SEARCH_ENDPOINT"],
                        "index_name": os.environ["AZURE_SEARCH_INDEX"],
                        "authentication": {
                            "type": "api_key",
                            "key": os.environ["AZURE_SEARCH_KEY"],
                        }
                    }
                }
            ],
        }
     )
    ```

      >**Note**: Ensure that the indentation is correct after pasting the code into the editor; it should align with the previous line.

1. Press **Ctrl + S** on your keyboard to save the file.

## Task 8: Run your application

In this task, you will run your configured app to send a request to your model and observe the response, noting that the only difference between options is the prompt content while all other parameters (such as token count and temperature) remain consistent.

In this task, you will run the reviewed code to generate some images.

1. In the Cloud Shell bash terminal, navigate to the folder for your preferred language.

2. In the interactive terminal pane, ensure the folder context is the folder for your preferred language. Then enter the following command to run the application.

    - **C#**: `dotnet run`
    - **Python**: `python ownData.py`

     >**Note**: If you encounter any errors after running the Python script, try upgrading the OpenAI package by running the following command:
        
    ```
    pip install --user --upgrade openai
    ```

    > **Tip**: You can use the **Maximize panel size** (**^**) icon in the terminal toolbar to see more of the console text.

3. Review the response to the prompt `Tell me about London`, which should include an answer as well as some details of the data used to ground the prompt, which was obtained from your search service.

   ![](../media/final-response-2107.png "upload files")
   
### Summary

In this lab, you have accomplished the following:
-   Provisioned an Azure OpenAI resource
-   Deployed an OpenAI model within the Azure AI Foundry portal
-   Used the power of OpenAI models to generate responses limited to custom ingested data.

### You have successfully finished the lab. Click **Next** to continue to the next lab.

   ![Launch Azure Portal](../media/next-page-2107.png)
