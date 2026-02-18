## Add your data for RAG with Azure OpenAI Service

## Lab scenario
The Azure OpenAI Service enables you to use your own data with the intelligence of the underlying LLM. You can limit the model to only use your data for pertinent topics, or blend it with results from the pre-trained model.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Deploy a model
- Task 3: Observe normal chat behavior without adding your own data
- Task 4: Connect your data in the chat playground
- Task 5: Chat with a model grounded in your data
- Task 6: Set up an application in Cloud Shell
- Task 7: Configure your application
- Task 8: Run your application

## Estimated time: 60 minutes

### Task 1: Provision an Azure OpenAI resource

In this task , you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **Azure portal**, search for **Azure OpenAI** and select **Azure OpenAI**.

   ![](../media/tel-11.png)

1. On the **Microsoft Foundry | Azure OpenAI** page, Click on **+ Create (1)** from the list, select **Azure OpenAI (2)**

   ![](../media/uupimg1.png)

1. Create an **Azure OpenAI** resource with the following settings click on **Next** three times and subsequently click on **Create**:
   
    - **Subscription**: Default - Pre-assigned subscription.
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Region**: <inject key="Region" enableCopy="false" />
    - **Name**: OpenAI-Lab06-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Pricing tier**: Standard S0

      ![](../media/azopenai123.png "Create Azure OpenAI resource")

1. Wait for deployment to complete. Then go to the deployed Azure OpenAI resource in the Azure portal.

1. If you are not able to see the left menu, click on **Service menu**.

   ![](../media/uupimg2.png) 

1. To capture the Keys and Endpoints values, on **openai-<inject key="DeploymentID" enableCopy="false"></inject>** blade:
      - Select **Keys and Endpoint (1)** under **Resource Management**.
      - Click on **Show Keys (2)**.
      - Copy **Key 1 (3)** and ensure to paste it in a text editor such as notepad for future reference.
      - Finally copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as notepad for later use.

        ![](../media/ui3.png "Keys and Endpoints")

<validation step="cafb7718-6bf1-4fe9-88b8-d1ed6d7c4c58" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 2: Deploy a model

In this task, you'll deploy a specific AI model instance within your Azure OpenAI resource to integrate advanced language capabilities into your applications.

1. On **Microsoft Foundry | Azure OpenAI** blade, select **OpenAI-Lab06-<inject key="DeploymentID" enableCopy="false"></inject>**

   ![](../media/uupimg3.png)

1. In the Azure OpenAI resource pane, click on **Go to Foundry portal** it will navigate to **Microsoft Foundry portal**.

   ![](../media/uupimg4.png)

1. Click on **Deployments (1)** under **Shared 
   Resources**, then select **+ Deploy Model (2)**. Next, choose **Deploy Base Model (3).**

      ![](../media/uupimg5.png)

1. Search for **gpt-4.1-mini (1)**, click on **Confirm (2)**

      ![](../media/uupimg6.png)
   
1. Within the Deploy model pop-up interface, enter the following details:
      - Deployment name: text-turbo
      - Deployment type: Standard
      - Click on Customize
      - Tokens per Minute Rate Limit (thousands): 20K
      - Click on Deploy
  
           ![](../media/uupimg7.png)
           ![](../media/uupimg8up.png) 

1. Click on the **Create** button to deploy a model which you will be playing around with as you proceed.

<validation step="863492e4-6930-40bf-ab9f-e1ffb7e21a95" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 3: Observe normal chat behavior without adding your own data

Before connecting Azure OpenAI to your data, first observe how the base model responds to queries without any grounding data.

1. In the **Playground** section, select the **Chat** page. The **Chat** playground page consists of three main sections:
     - **Setup** - used to configure settings for the model deployment.
     - **Give the model instructions and context** - used to set the context for the model's responses.
    - **Chat session** - used to submit chat messages and view responses.

      ![](../media/uupimg9.png)

1. In the **Chat session**, submit the following queries, and review the responses:

    ```
    I'd like to take a trip to New York. Where should I stay?
    ```

    ```
    What are some facts about New York?
    ```

    Try similar questions about tourism and places to stay for other locations that will be included in our grounding data, such as London, or San Francisco. You'll likely get complete responses about areas or neighborhoods, and some general facts about the city.

### Task 4: Connect your data in the chat playground

In this task, you will observe how the base model responds to queries without any grounding data before connecting Azure OpenAI to your data.

1. Copy the URL (https://github.com/CloudLabsAI-Azure/mslearn-openai-data/blob/5d0e51c7c8d42b90612a0c4809bb7582a721acd0/Labfiles/02-use-own-data/data/brochures.zip) and paste it in the browser. 

1. Once the github window is opened, click on the download button as shown to download the datasets (brouchers.zip) file and extract it in your labvm.

   ![](../media/uupimg19.png)
   
1. In the **Azure portal**, search for **Storage Account** and select **Storage accounts**.

   ![](../media/1.png)

1. On **Storage Account** page, click on **Create**.

   ![](../media/2.png)

1. Create a **Storage Account** resource with the following settings:

    - **Subscription**: Default - Pre-assigned subscription
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Storage account name**: storage<inject key="DeploymentID" enableCopy="false"></inject>
    - **Region**: Select <inject key="Region" enableCopy="false" />
    - **Preffered storage type**: Azure Blob Storage or Azure Lake Storage Gen 2
    - **Redundancy**: Locally-redundant storage (LRS)
    - Click **Next**.
  
      ![](../media/uupimg11.png)
      ![](../media/uupimg12.png)

    - **Allow enable anonymous access on individual containers**: check in the box to enable under **Advanced** section. Click on **Review + Create**  and subsequently click on **Create**

      ![](../media/image4.5.png "allow blob access")

1. Wait until the storage account is created before you proceed to the next task. This should take about a minute.

1. On the deployment blade, click **Go to resource**.

    ![](../media/3.png "upload files")

1. On **Storage Account | Container** blade, select **Containers** from Data Storage and click on **+ Add Container**.

     ![](../media/uupimg14.png)

1. Create a container with the name **openaidatasource** and enable Anonymous access level for container.

      ![](../media/image4.6.png "create container")

1. Click on the container you just created and 
 upload all the files into the container which are downlaoded and extracted during the first step of Task 4.

      ![](../media/image4.7.png "upload files")

1. In the **Azure portal**, search for **Azure AI search** and select **Azure AI search**.

     ![](../media/uupimg15.png)

1.  On **Azure AI services | AI search** blade, click on **+ Create**.

     ![](../media/5.png "upload files")

1. Create an **AI Search** resource with the following settings and click on **Review + Create** and subsequenly click on **Create**

    - **Subscription**: Default - Pre-assigned subscription
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Service name**: cognitive-search-<inject key="DeploymentID" enableCopy="false"></inject>
    - **Location**:Select <inject key="Region" enableCopy="false" />
    - **Pricing tier**: Basic

      ![](../media/openai-lab06_t4_s5.png "Create cognitive search resource")

1. Wait until your search resource has been deployed.

1. Navigate to the **cognitive-search-<inject key="DeploymentID" enableCopy="false"></inject>** and in the overview page copy the URL and paste it in a text editor such as notepad for later use.

    ![](../media/x689.png)

1. From the left navigation pane,click on **Keys** under Settings and copy the primary key or secondary key and paste it in a notepad file for later use.

      ![](../media/x690.png)

1. In **Microsoft Foundry portal**, Navigate to the **Chat**(1) playground followed by select *Add your data*(2) in the setup pane and click on **+ Add a data source**(3).

    ![](../media/uupimg16.png)

    >If you are not able to see this option, please click on **Show Setup** icon to see the setup menu.

    ![](../media/uupimg10.png)

1. In the **Add data**, enter the following values for your data source and then click on **Next**.

    - **Select data source**: Azure Blob Storage(preview)
    - **Select Azure Blob storage resouce**: *Choose the storage resource you created*
    - **Select storage container**: *Choose the storage container you created*
    - **Select Azure AI Search resource**: *Choose the search resource you created*
    - **Enter the index name**: margiestravel
    - **Indexer schedule**: Once
   
       ![](../media/image4.8.png "Add data configurations")

1. Click on next to proceed with **Data Management**
   
1. On the **Data management** page select the **Keyword** search type from the drop-down, and then select **Next**.

    ![](../media/datamanagement.png "Add data")

1. On the **Data connection** page select the **API key** , Click on the **Next**

    ![](../media/API_key.jpg "Add data")
   
1. On the **Review and finish** page select **Save and close**, which will add your data. This may take a few minutes, during which you need to leave your window open. Once completed, verify if the data source, search resource, and index specified **margiestravel** is present under the **Add your data** tab in **setup** pane.

    ![](../media/review.jpg "Add data")

<validation step="cf9a74ba-2501-47a6-a819-b42218c0a9da" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 5: Chat with a model grounded in your data

In this task, you will ask the same questions as before after adding your data, and observe how the responses differ.

   ```
   I'd like to take a trip to New York. Where should I stay?
   ```

   ```
   What are some facts about New York?
   ```

You'll notice a very different response this time, with specifics about certain hotels and a mention of Margie's Travel, as well as references to where the information provided came from. If you open the PDF reference listed in the response, you'll see the same hotels as the model provided.

Try asking it about other cities included in the grounding data, which are Dubai, Las Vegas, London, and San Francisco.

### Task 6: Set up an application in Cloud Shell

In this task, you will use a short command-line application running in Cloud Shell on Azure to demonstrate integration with an Azure OpenAI model. Open a new browser tab to access Cloud Shell.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

      ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/cloudshell-launch-portal.png)

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**.

    ![](../media/uupimg17.png)

1. Within the Getting Started pane, select **Mount storage account**, select your **Storage account subscription** from the dropdown and click **Apply**.

      ![](../media/cloudshell-getting-started.png)

1. Within the **Mount storage account** pane, select **I want to create a storage account** and click **Next**.

      ![](../media/cloudshell-mount-strg-account.png)

1. Within the **Advanced settings** pane, enter the following details:

    - **Subscription**: Default- Choose the only existing subscription assigned for this lab (1).
    - **Resource group**: openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)
    - **Region**: Select <inject key="Region" enableCopy="false" /> (3)
    - **Storage account name**: str<inject key="DeploymentID" enableCopy="false"></inject> (4)
    - **File share**: Create a new file share named **none** (5)
    - Click **Create** (6)

        ![](../media/uupimg18.png)

1. Make sure the type of shell indicated on the top left of the Cloud Shell pane is switched to *Bash*. If it's *PowerShell*, switch to *Bash* by using the drop-down menu.

1. Once the terminal opens, click on **Settings** and select **Go to Classic Version**.

   ![](../media/classic-cloudshell.png)

1. Once the terminal starts, enter the following command to download the sample application and save it to a folder called `azure-openai`.

    ```bash
   rm -r azure-openai -f
   git clone https://github.com/CloudLabsAI-Azure/mslearn-openai-data.git azure-openai
    ```

1. The files are downloaded to a folder named **azure-openai**. Navigate to the lab files for this exercise using the following command.

    ```bash
   cd azure-openai/Labfiles/02-use-own-data
    ```

    Applications for both C# and Python have been provided, as well as sample code we'll be using in this lab.

1. Open the built-in code editor, and you can observe the code files we'll be using in `sample-code`. Use the following command to open the lab files in the code editor.

    ```bash
    code .
    ```  

### Task 7: Configure your application

In this task, you will complete key parts of the application to enable it to use your Azure OpenAI resource.

1. In the code editor, expand the language folder for your preferred language.


1. Navigate to the folder for your preferred language and install the necessary packages.

    **C#**:

    ```
    cd CSharp
    export DOTNET_ROOT=$HOME/.dotnet
    export PATH=$DOTNET_ROOT:$PATH
    mkdir -p $DOTNET_ROOT
    ```     

    > **Note**: Azure Cloud Shell often does not have admin privileges, so you need to install .NET in your home directory. So here Your creating a separate `.dotnet` directory under your home directory to isolate your configuration.
    - `DOTNET_ROOT` specifies where your .NET runtime and SDK are located (in your `$HOME/.dotnet directory`).
    - `PATH=$DOTNET_ROOT:$PATH` ensures that the locally installed .NET SDK can be accessed globally by your terminal.
    - `mkdir -p $DOTNET_ROOT` this creates the directory where the .NET runtime and SDK will be installed.

1. Run the following command to install the required SDK version locally:     

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

1. Navigate to the folder for your preferred language and install the necessary packages.

     **C#**:

    ```
    cd CSharp
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.14
    dotnet add package Azure.AI.OpenAI --prerelease
    dotnet add package Azure.Search.Documents
    ```

    **Python**:

    ```
    cd Python
    pip install python-dotenv --user
    pip install openai==1.56.2 --user
    ```

1. In the code editor from the left navigation pane, in the **CSharp** or **Python** folder, open the configuration file for your preferred language

    - **C#**: appsettings.json
    - **Python**: .env

1. Update the configuration values to include:
    - The  **endpoint** and a **key** from the Azure OpenAI resource you created (Which you copied in the previous task alternatively it is available on the **Keys and Endpoint** page for your Azure OpenAI resource in the Azure portal)
    - The **deployment name** you specified for your model deployment (available in the **Deployments** page in Microsoft Foundry portal that is **text-turbo**).
    - The endpoint for your AI search service (Which you copied in the previous task alternatively it is available in the **Url** value on the overview page for your AI search resource in the Azure portal).
    - A **key** for your search resource (available in the **Keys** page for your AI search resource in the Azure portal - you can use either of the admin keys)
    - The name of the search index (which should be `margiestravel`).

         ![](../media/x676.png)

1. Open the code file for your preferred language, and replace the comment ***Configure your data source*** with code to add the Azure OpenAI SDK library:

    **C#**: ownData.cs

    ```csharp
    AzureSearchChatDataSource ownDataConfig = new()
    {
        Endpoint = new Uri(azureSearchEndpoint),
        Authentication = DataSourceAuthentication.FromApiKey(azureSearchKey),
        IndexName = azureSearchIndex
    };
    ```

    **Python**: ownData.py

    ```python
    # Configure your data source
    extension_config = {
        "data_sources": [
            {
                "type": "azure_search",
                "parameters": {
                    "endpoint": azure_search_endpoint,
                    "index_name": azure_search_index,
                    "authentication": {
                        "type": "api_key",
                        "key": azure_search_key,
                    }
                }
            }
        ]
    }
    ```
    > **Note**: Ensure that the indentation is correct when copying and pasting the Python code.

1. Review the rest of the code, noting the use of the *extensions* in the request body that is used to provide information about the data source settings.

1. Save the changes to the code file.

## Task 8: Run your application

In this task, you will run your configured app to send a request to your model and observe the response, noting that the only difference between options is the prompt content while all other parameters (such as token count and temperature) remain consistent.

In this task, you will run the reviewed code to generate some images.

1. In the Cloud Shell bash terminal, navigate to the folder for your preferred language.

1. In the interactive terminal pane, ensure the folder context is the folder for your preferred language. Then enter the following command to run the application.

    - **C#**: `dotnet run`
    - **Python**: `python ownData.py`

    > **Tip**: You can use the **Maximize panel size** (**^**) icon in the terminal toolbar to see more of the console text.

1. Review the response to the prompt `Tell me about London`, which should include an answer as well as some details of the data used to ground the prompt, which was obtained from your search service.

## Summary

In this lab, you have accomplished the following:
-   Provisioned an Azure OpenAI resource
-   Deployed an OpenAI model within the Microsoft Foundry portal
-   Used the power of OpenAI models to generate responses limited to a custom ingested data.

### You have successfully completed the lab.
