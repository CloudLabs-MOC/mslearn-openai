# Lab: Add your data for RAG with Azure OpenAI Service

## Estimated Duration: 90 Minutes

## Lab Overview

In this lab, you will learn how to implement Retrieval-Augmented Generation (RAG) using Azure OpenAI Service. You will provision an Azure OpenAI resource, deploy a language model, and observe how the model responds before and after connecting it to your own data. You will store documents in Azure Blob Storage, index them using Azure AI Search, and connect the data source in the Chat playground. Finally, you will configure and run a sample application in Cloud Shell to query the model using your indexed data.

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

### Task 1:  Provision an Azure OpenAI resource

In this task , you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **[Azure portal](https://portal.azure.com/)**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)**.

      ![](../media/l1-12-0.png)

2. On the **Microsoft Foundry | Azure OpenAI** page, select **Azure OpenAI (1)** from the left pane, click **+ Create (2)** drop-down and click on **Azure OpenAI (3)**.

     ![](../media/va1.png)

3. Create an **Azure OpenAI** resource with the following settings, click on **Next (6)** thrice and subsequently click on **Create**:
   
      - **Subscription:** Default - Pre-assigned subscription. **(1)**
      - **Resource group:** **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
      - **Region:** Select **<inject key="Region" enableCopy="false" /> (3)**
      - **Name:** **OpenAI-Lab06-<inject key="DeploymentID" enableCopy="false"></inject> (4)**
      - **Pricing tier**: Standard S0 **(5)**

        ![](../media/l3-12-0.png)

        >**Note:** DALL-E 3 models are only available in Azure OpenAI service resources in the **East US** and **Sweden Central** regions.

1. Wait for deployment to complete. Click on **Go to resource** to navigate to the deployed Azure OpenAI resource in the Azure portal.

     ![](../media/l1-12-2.png)

5. To capture the Keys and Endpoints values, on **openai-<inject key="DeploymentID" enableCopy="false"></inject>** blade:
      - Select **Keys and Endpoint (1)** under **Resource Management**.
      - Click on **Show Keys (2)**.
      - Copy **Key 1 (3)** and ensure to paste it into a text editor such as Notepad for future reference.
      - Finally, copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as Notepad for later use.

        ![](../media/e1t1p5a.png "Keys and Endpoints")

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="cafb7718-6bf1-4fe9-88b8-d1ed6d7c4c58" />

### Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. In the **Azure portal**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)**.

      ![](../media/l1-12-0.png)

2. On the **Microsoft Foundry | Azure OpenAI** page, ensure that **Azure OpenAI (1)** is selected from the left blade. Then, select **OpenAI-Lab06-<inject key="DeploymentID" enableCopy="false"></inject>(2)**

      ![](../media/l5-12-1.png)

3. In the Azure OpenAI resource pane, click on **Go to Foundry portal**, which will navigate to the **Microsoft Foundry portal**.

      ![](../media/l5-12-2.png)

1. Select the **Deployments (1)** from the left pane, click on **+ Deploy model (2)** and choose **Deploy base model (3)**.

    ![](../media/l6-12-1.png)

1. Search for **gpt-4.1-mini (1)** in the search bar, select **gpt-4.1-mini (2)** and click on **Confirm (3)**.

   ![](../media/l1-12-3.png) 

   >**Note:** If pop-up window **Unlock the full capabilities of Azure Microsoft Foundry with projects** appears, click **Continue with existing setup**

      ![](../media/e1t2p2(1).png)
   
1. Within the **Deploy model gpt-4.1-mini** pop-up interface, click on **Customize**.

   ![](../media/custom4.1.png)

1. Within the **Deploy model gpt-4.1-mini** pop-up interface, enter the following details:

      - Deployment name: **text-turbo (1)**

      - Deployment type: **Standard (2)**

      - Model version: **2025-04-14 (Default) (3)**

      - Tokens per Minute Rate Limit (thousands): **10K (4)**

      - Content filter: **DefaultV2 (5)**

      - Enable dynamic quota: **Enabled (6)**

      - Click on **Deploy (7)**

        ![](../media/l6-12-2.png)


<validation step="863492e4-6930-40bf-ab9f-e1ffb7e21a95" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
        
## Task 3: Observe normal chat behavior without adding your own data

In this task, you will observe how the base model responds to queries without any grounding data.

1. In [Microsoft Foundry portal](https://oai.azure.com/?azure-portal=true), navigate to the **Chat (1)** section under **Playgrounds** in the left pane.

2. In the **Deployment** section in Chat page, ensure that your model deployment **text-turbo (2)** is selected.

   ![](../media/l3-12-1.png)

4. In the **Chat session** on the right side, submit the following queries, and review the responses:

    ```
    I'd like to take a trip to New York. Where should I stay?
    ```

   ![](../media/lab6-02-1.png)

    ```
    What are some facts about New York?
    ```

   ![](../media/lab6-02-2.png)

    Try similar questions about tourism and places to stay for other locations that will be included in our grounding data, such as London or San Francisco. You'll likely get complete responses about areas or neighbourhoods, and some general facts about the city.

## Task 4: Connect your data in the chat playground

In this task, you will observe how the base model responds to queries without any grounding data before connecting Azure OpenAI to your data.
   
1. On the Azure portal, type **Storage account (1)** in the search box and select **Storage accounts (2)** from the results.

   ![](../media/strgact.png)

1. On **Storage Centre | Blob Storage** page, select **+ Create**.

   ![](../media/lab6-02-3.png)

1. On the **Create a storage account** page, under the **Basic** tab, enter the following details and click on **Next (7)**:

   | Settings | Action |
   | -- | -- |
   | **Subscription** | Default - Pre-assigned subscription **(1)** |
   | **Resource group** | **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)** |
   | **Storage account name** | **storage<inject key="DeploymentID" enableCopy="false"></inject> (3)** |
   | **Region** | Select **<inject key="Region" enableCopy="false" /> (4)** |
   | **Primary Service** | Azure Blob Storage or Azure Data Lake Storage Gen 2 **(5)** |
   | **Redundancy** | Locally-redundant storage (LRS) **(6)** |
  
    ![](../media/l6-12-3.png)

1. Under the **Advanced** tab, provide the following details:

   | Settings | Action |
   | -- | -- |
   | **Allow enable anonymous access on individual containers (1)** | Check in the box. |

1. Click on **Review + create (2)** and subsequently click on **Create**. 

    ![](../media/advstrg.png)

1. Wait until the storage account is created before you proceed to the next task. This should take about a minute.

1. Once the deployment is successful, click **Go to resource**.

    ![](../media/gtr.png)

1. On **Storage Account**, go to **Container (1)** section under **Data Storage** and click on **+ Add Container (2)** to create a new container.

    ![](../media/lab6-02-4.png)

1. On the **New container** creation page, enter the container name as **openaidatasource (1)**, then set the **Anonymous access level** to **Container (anonymous read access for containers and blobs) (2)**. Once both fields are configured, click on the **Create (3)** button..

    ![](../media/newcon.png)

1. Open the **openaidatasource** container page, click on the **Upload** button located at the top to begin uploading files to the container.

    ![](../media/L6T2S9-0205-1.png "upload files")

1. On the **Upload blob** pane, click on **Browse for files** to select the file you want to upload.

    ![](../media/bff.png)

1. Search for and go to location `C:\AllFiles\mslearn-openai-main\Labfiles\06-use-own-data\data` **(1)**. Select all the **PDF files (2)** and click on **Open (3)**. Then click on **Upload** to upload all PDF files. 

    ![](../media/l6-12-4.png)

1. Verify the **openaidatasource** container after all files are uploaded.

    ![](../media/fileuploaded.png)

1. On the Azure portal, type **AI Search (1)** in the search box and select **AI Search (2)** from the results.

    ![](../media/aisrchportal.png)

1. On **Microsoft Foundry | AI search** blade, click on **+ Create**.

    ![](../media/l6-12-5.png)

1. On the **Create an AI Search** resource page, enter the following settings under the **Basics** tab and click on **Review + create (5)**.

   | Settings | Action |
   | -- | -- |
   | **Subscription** | Default - Pre-assigned subscription |
   | **Resource group** | **openai-<inject key="DeploymentID" enableCopy="false"></inject> (1)** |
   | **Service name** | **cognitive-search-<inject key="DeploymentID" enableCopy="false"></inject> (2)** |
   | **Location** | Select **<inject key="Region" enableCopy="false" /> (3)** |
   | **Pricing tier** | Change the Pricing tier to **Basic (4)** |

   ![](../media/reviewaisrch2.png)
   
    > **Note:** If **East US** is not available due to high demand, select **East US 2**, **Australia East**, or any other available supported region.

1. Then click on **Create**.

    ![](../media/lab6-02-5.png)

1. Once the deployment is successful, click on **Go to resource** to go to the deployed search service. 

   ![](../media/2gtrai.png)

1. Navigate to the **cognitive-search-<inject key="DeploymentID	" enableCopy="false"></inject>** and in the overview page, copy the URL and paste it in a text editor such as Notepad for later use.

    ![](../media/cogurl.png)

1. From the left navigation pane, under **Settings (1)** click on **Keys (2)** and **copy the primary key or secondary key (3)** and paste it into a notepad for later use.

    ![](../media/cogkeys.png)

1. In **Microsoft Foundry portal**, navigate to the **Chat (1)** section under **Playgrounds** followed by select **Add your data (2)** in the setup pane and click on **+ Add a data source (3)**.

    ![](../media/l6-12-6.png)
   
1. On the **Add data** window, enter the following values for under the **Data source** and then click on **Next (7)** to proceed with **Data Management**.

   | Setting | Action |
   | -- | -- |
   | **Select data source** | Azure Blob Storage (preview) **(1)** |
   | **Select Azure Blob storage resource** | *Choose the storage resource **storage1<inject key="DeploymentID" enableCopy="false"></inject> (2)** you created* (If it isn’t visible, try clicking Refresh next to the storage account) |
   | **Select Storage container** | **openaidatasource (3)** |
   | **Select Azure AI Search resource** | *Choose **cognitive-search-<inject key="DeploymentID	" enableCopy="false"></inject> (4)** search resource you created* |
   | **Enter the index name** | **margiestravel (5)** |
   | **Indexer schedule** | **Once (6)** |
   
    ![](../media/addds.png)
   
1. On the **Data management** page select the **Keyword (1)** search type from the drop-down, and then select **Next (2)**.

    ![](../media/dmnext.png)

1. On the **Data connection** page select the **API key (1)** , Click on the **Next (2)**

    ![](../media/dconcn.png)
   
1. On the **Review and finish** page select **Save and close**, which will add your data.

    ![](../media/refin.png)

1. This may take a few minutes, during which you need to keep your window open.
       
    ![](../media/ingprcs.png)
  
1. Once completed, verify if the data source, search resource, and index specified **margiestravel** are present under the **Add your data** tab in the  **Assistant setup** pane.

    ![](../media/lab6-02-6.png)   

<validation step="cf9a74ba-2501-47a6-a819-b42218c0a9da" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.


## Task 5: Chat with a model grounded in your data

In this task, you will ask the same questions as before in the chat section after adding your data, and observe how the responses differ.

1. In the **Chat** session on the right side, submit the following queries, and review the responses:

   ```
   I'd like to take a trip to New York. Where should I stay?
   ```

   ![](../media/lab6-02-7.png)

   ```
   What are some facts about New York?
   ```

   ![](../media/lab6-02-8.png)

2. You'll notice a very different response this time, with specifics about certain hotels and a mention of Margie's Travel, as well as references to where the information provided came from. If you open the PDF reference listed in the response, you'll see the same hotels as the model provided. Try asking it about other cities included in the grounding data, which are Dubai, Las Vegas, London, and San Francisco.

    >**Note:** **Add your data** is still in preview and might not always behave as expected for this feature, such as giving the incorrect reference for a city not included in the grounding data.

## Task 6: Set up an application in Cloud Shell

In this task, you will use a short command-line application running in Cloud Shell on Azure to demonstrate integration with an Azure OpenAI model. Open a new browser tab to access Cloud Shell.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_] (Cloud Shell)** button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![](../media/cshell.png)

    >**Note:** If you can't find Cloud Shell, click on the **ellipsis (...) (1)** and then select **Cloud Shell (2)** from the menu.

    ![](../media/180625(14).png)

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**. If you don't see this option, skip the step.

     ![](../media/bash.png)

1. Within the **Getting started** page, select **Mount storage account (1)**, select your **Subscription (2)** from the dropdown and click **Apply (3)**.

     ![](../media/lab3-02-4.png)

1. Within the **Mount storage account** page, select **I want to create a storage account (1)** and click **Next (2)**.

    ![](../media/csanext.png)

1. Within the **Create storage account** page, enter the following details:

    - **Subscription:** Default - Pre-assigned subscription **(1)**.
    - **Resource group:** **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    - **Region:** Select **<inject key="Region" enableCopy="false" /> (3)**
    - **Storage account name:** **stg<inject key="DeploymentID" enableCopy="false"></inject> (4)**
    - **File share:** none **(5)**
    - Click **Create (6)**

      ![](../media/l5-12-st.png)

3. Once the terminal opens, click on **Settings (1)** and select **Go to Classic version (2)**.

   ![](../media/classic.png)

4. In the cloud shell pane, enter the following commands to clone the GitHub repo containing the code files for this exercise.

     ```
     rm -r mslearn-openai -f
     git clone https://github.com/microsoftlearning/mslearn-openai mslearn-openai
     ```

5. After the repo has been cloned, navigate to the folder containing the chat application code files
   
    ```bash
    cd mslearn-openai/Labfiles/02-use-own-data
    ```

    Applications for both C# and Python have been provided, as well as sample code we'll be using in this lab.

5. Open the built-in code editor, and you can observe the code files we'll be using in `sample-code`. Use the following command to open the lab files in the code editor.

    ```bash
   code .
    ```

## Task 7: Configure your application

In this task, you will complete key parts of the application to enable it to use your Azure OpenAI resource.

1. In the code editor, expand the language folder for your preferred language.

1. Open the configuration file for your language.

    - **C#**: `appsettings.json`
    - **Python**: `.env`

1. Update the configuration file for your chosen language with the following values:

    - **Azure OpenAI endpoint**: Paste the endpoint URL from your Azure OpenAI resource (found on the Keys and Endpoint page in the Azure portal).
    - **Azure OpenAI key**: Paste the key from your Azure OpenAI resource (also on the Keys and Endpoint page).
    - **Deployment name**: Enter the name of your model deployment (e.g., `text-turbo` from the Deployments page in the Azure Microsoft Foundry portal).
    - **Azure AI Search endpoint**: Paste the endpoint URL for your AI Search service (copied earlier or found in the overview page for your AI Search resource).
    - **Azure AI Search key**: Paste the admin key for your AI Search resource (available on the Keys page).
    - **Search index name**: Enter `margiestravel` as the index name.
    - Save your changes after updating these values.

        ![](../media/l6-12-7.png)

1. If you're using **C#**, navigate to `CSharp.csproj`, delete the existing code, then replace it with the following code, and then press **Ctrl+S** to save the file.

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

    ![](../media/L6T5S4-1807.png)    

1. Navigate to the **CSharp** folder and install the necessary packages. These commands set up the environment for a local installation of the .NET SDK in Cloud Shell.

    ```
    cd CSharp
    export DOTNET_ROOT=$HOME/.dotnet
    export PATH=$DOTNET_ROOT:$PATH
    mkdir -p $DOTNET_ROOT
    ```   

    - `DOTNET_ROOT` specifies where your .NET runtime and SDK are located (in your `$HOME/.dotnet directory).
    - `PATH=$DOTNET_ROOT:$PATH` ensures that the locally installed .NET SDK can be accessed globally by your terminal.
    - `mkdir -p $DOTNET_ROOT` This creates the directory where the .NET runtime and SDK will be installed.

1. Run the following command to install the required SDK version locally. These commands download and prepare the official `.NET` installation script, grant it execute permissions, and install the required .NET SDK version (8.0.404) in the `$DOTNET_ROOT` directory, as we don't have the admin privileges to install it globally.    

     ```
     wget https://dotnet.microsoft.com/download/dotnet/scripts/v1/dotnet-install.sh
     chmod +x dotnet-install.sh
     ./dotnet-install.sh --version 8.0.404 --install-dir $DOTNET_ROOT
     ``` 

1. Enter the following command to restore any required workloads for your project, such as additional tools or libraries that are part of the .NET SDK.

    ```
    dotnet workload restore
    ```

1. Enter the following command to add the `Azure.AI.OpenAI` NuGet package to your project, which is necessary for integrating with Azure OpenAI services.

    ```
    dotnet add package Azure.AI.OpenAI --version 2.1.0
    dotnet add package Azure.Search.Documents --version 11.6.0
    ```

1. If you prefer **Python**, navigate to the **Python** folder and install the necessary packages using the commands below:

    ```
    cd Python
    python -m venv labenv
    ./labenv/bin/Activate.ps1
    pip install --user python-dotenv openai==1.65.2
    ```

1. In the code editor, replace the comment **Configure your data source** with code to your index as a data source for chat completion:

    For **C#**: OwnData.cs

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

    ![](../media/l6-12-8.png)

    For **Python**: ownData.py

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

    ![](../media/l6-12-9.png)

1. Save the changes to the code file.

## Task 8: Run your application

In this task, you will run your configured app to send a request to your model and observe the response, noting that the only difference between options is the prompt content while all other parameters (such as token count and temperature) remain consistent.

In this task, you will run the reviewed code to generate some images.

1. In the **Cloudshell** bash terminal, navigate to the folder for your preferred language.

2. In the interactive terminal pane, ensure the folder context is the folder for your preferred language. Then enter the following command to run the application.

    - **C#**: `dotnet run`
    - **Python**: `python ownData.py`

        >**Note**: If you encounter any errors after running the Python script, try upgrading the OpenAI package by running the following command:
        
        ```
        pip install --user --upgrade openai
        ```

3. Review the response to the prompt `Tell me about London`, which should include an answer as well as some details of the data used to ground the prompt, which was obtained from your search service.

    ![](../media/l6-12-10.png)

## Summary

In this lab, you provisioned an Azure OpenAI resource, deployed a model, and observed the model’s responses without grounding data. You then uploaded documents to Azure Blob Storage, indexed them with Azure AI Search, and connected the data source to enable RAG-based responses. Finally, you configured and ran an application in Cloud Shell to query the model using your connected data.

### Congratulations on completing the lab! Click Next >> to continue to the next lab.

![Launch Azure Portal](../media/l5-next.png)
