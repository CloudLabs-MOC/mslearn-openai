# Lab 05: Generate images with a gpt-image-1-mini model

## Estimated Duration: 60 minutes

## Lab scenario
The Azure OpenAI Service includes an image-generation model named gpt-image-1-mini. You can use this model to submit natural language prompts that describe a desired image, and the model will generate an original image based on the description you provide.

In this exercise, you'll use a gpt-image-1-mini model to generate images based on natural language prompts.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1: Provision a Microsoft Foundry resource
- Task 2: Explore image-generation in the gpt-image-1-mini playground 
- Task 3: Use the REST API to generate images 
- Task 3.1: Prepare the app environment
- Task 3.2: Configure your application
- Task 3.3: View application code
- Task 4: Run the app 

### Task 1:  Provision a Microsoft Foundry resource

In this task , you'll create an Azure resource in the Azure portal, selecting the Microsoft Foundry service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **Azure portal**, search for **Microsoft Foundry (1)** and select **Microsoft Foundry (2)** from the results.

   ![](../media/mf-1.png)

1. On the **Microsoft Foundry** overview pane, select **Create a resource**

   ![](../media/mf-2.png)

1. Create an **Foundry** resource using the settings below, then click **Review + create (6)** , leaving all other options at their defaults.
    
    - Subscription: **Default Subscription (1)**
    
    - Resource group: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    
    - Name: **OpenAI-Lab05-<inject key="DeploymentID" enableCopy="false"></inject> (3)**

    - Region: **<inject key="Region" enableCopy="false"></inject> (4)**
    
    - Default project name: **proj-default (5)**
  
      ![](../media/mf-3.png)

1. Under the **Review + create** tab, click on **Create**.

1. Wait for deployment to complete. Click on **Go to resource** to navigate to the deployed Azure OpenAI resource in the Azure portal.

      ![](../media/mf-4.png)

1. To capture the Keys and Endpoints values, on **OpenAI-Lab05-<inject key="DeploymentID" enableCopy="false"></inject>** blade:

    - On the left navigation menu, expand **Resource Management** and select **Keys and Endpoint (1)**.
    
    - Copy **Key 1 (2)** and ensure to paste it in a text editor such as notepad for future reference.
    
    - Select **OpenAI (3)**, copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as notepad for later use.
    
        ![](../media/mf-5.png "Keys and Endpoints")

<validation step="d1fdf614-83d8-4c1a-b9c7-c9adf003d03f" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

## Task 2: Explore image generation in the gpt-image-1-mini playground 

In this task, you will use the gpt-image-1-mini playground in the Microsoft Foundry portal to experiment with image generation.

1. In the Azure Microsoft Foundry resource pane, click on **Go to Foundry portal**, which will navigate to the **Microsoft Foundry portal**.

      ![](../media/mf-6.png)

1. Click **View deployments** under Use a model.

    ![](../media/SS-1.png)

1. On Deployments tab, click **Deploy (1)**, and choose **Deploy a base model (2)**.

     ![](../media/SS2.png)

1. Then, search **gpt-image-1-mini (1)** and choose **gpt-image-1-mini (2)**.

     ![](../media/a-1.png)

1. On the gpt-image-1-mini page, click on **Deploy (1)**, then select **Custom settings (2)**.

    ![](../media/a-2.png)

1. Within the **Deploy gpt-image-1-mini** pop-up interface, enter the following details:

      - Deployment name: **gpt-image-1-mini (1)**

      - Deployment type: **Global Standard (2)**

      - Requests per Minute Rate Limit (thousands): **3 (3)**

      - Guardrails: **DefaultV2 (4)**

      - Click on **Deploy (5)**

        ![](../media/a-3.png)
              
4. Now, enter a description of an image you'd like to generate in the **Describe the image you want to generate (1)** box (for example, `An elephant on a skateboard`), and then select **Generate (2)** to view the **resulting image (3)**.
   
      ![](../media/a-4.png)

      > **Note:** If you receive a **PermissionDenied** error, assign the required roles to your lab user by performing the following steps:
      >- In the Azure portal, navigate to your **OpenAI-Lab05-<inject key="DeploymentID" enableCopy="false"></inject>** foundry resource.
      >-  From the left menu, select **Access control (IAM)**, then select **+ Add** > **Add role assignment**.
      >- On the **Role** tab, search for and select **Cognitive Services OpenAI User**, then select **Next**.
      >- On the **Members** tab, keep **User, group, or service principal** selected, then click **+ Select members**.
      >- Search for and select your lab user **<inject key="AzureAdUserEmail"></inject>**, then click **Select**.
      >- Select **Review + assign**, then select **Review + assign** again.
      >- Repeat steps 2 to 6 to assign the **Azure AI Developer** role to the same user.
      >- Wait **5 minutes** for the role assignments to take effect, then refresh the browser.

1. Modify the prompt to provide a more specific description. For example, `An elephant on a skateboard in the style of Picasso` **(1)**. Then **generate (2)** the new image and review the **results (3)**.

      ![](../media/a-5.png)

      > **Note:** The image may appear differently than shown in the screenshot. 

## Task 3: Use the REST API to generate images 

The Azure OpenAI service provides a REST API that you can use to submit prompts for content generation, including images generated by a gpt-image-1-mini model.

### Task 3.1: Prepare the app environment

In this task, you will use a simple Python or C# app to generate images by calling the REST API and running the code in the Cloud Shell console interface within the Azure portal.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/GM3.png#lightbox)

    > **Note:** If a **Cloud Shell timed out** pop-up appears, click **Reconnect**.

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**. If you don't see this option, skip the step.

     ![](../media/bash11.png)

1. Within the **Getting started** page, select **Mount storage account (1)**, select your **Subscription (2)** from the dropdown and click **Apply (3)**.

     ![](../media/mountstrg1.png)

1. On the **Mount storage account** screen, select **I want to create a storage account (1)** and click on **Next (2)**.

    ![](../media/csanext1.png)

1. Provide the following details:

    - **Subscription**: Default - Pre-assigned subscription **(1)**.
    - **Resource group**: **openai-<inject key="Deployment-id" enableCopy="false"></inject> (2)**
    - **Region**: Select **<inject key="Region" enableCopy="false"></inject>  (3)**
    - **Storage account name**: **storage<inject key="Deployment-id" enableCopy="false"></inject> (4)**
    - **File share**: none **(5)**
    - Click **Create (6)**

      ![](../media/l5-12-st1.png)

1. Run the below commands:

    ```
    rm -r mslearn-openai -f
    git clone https://github.com/CloudLabs-MOC/mslearn-openai

    ```

1. Navigate to the folder for the language of your preference by running the appropriate command.

    **C#**

    ```bash
    cd mslearn-openai/Labfiles/05-image-generation/CSharp

    ```

    **Python**

    ```bash
    cd mslearn-openai/Labfiles/05-image-generation/Python

    ```

1. Use the following command to open the built-in code editor and see the code files you will be working with.

    ```bash
   code .
   ```

    ![](../media/l5-12-91.png)

### Task 3.2: Configure your application

In this task, you will use a configuration file in the application to store the details needed to connect to your Azure OpenAI service account.

1. In the code editor, select the configuration file for your app, depending on your language preference.

    - C#: `appsettings.json`
    - Python: `.env`
    
2. Update the configuration values to include the **Endpoint**, **Key1** and **Deployment name: gpt-image-1-mini** for your Azure OpenAI service. Then, save the file by right-clicking the file in the left pane.

    > **Tip:** You can adjust the split at the top of the cloud shell pane to see the Azure portal and get the endpoint and key values from the **Keys and Endpoint** page for your Azure OpenAI service.

3. If you are using **Python**, you'll also need to install the **python-dotenv** package used to read the configuration file. In the console prompt pane, ensure the current folder is **~/mslearn-openai/Labfiles/05-image-generation/Python**. Then enter this command:

    ```bash
   pip install python-dotenv
    ```
      > **Note:** If you receive a permission error after executing the installation command as shown in the image, please run the command below for installation/
      >    ![](../media/L2T3S9python-0205.png)
      > ```bash
      > pip install --user python-dotenv
      > ```

1. If you're using **C#**, navigate to `generate_image.csproj`, delete the existing code, then replace it with the following code and then press **Ctrl+S** to save the file. For pyhton move to step 9.

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
     <PackageReference Include="Microsoft.Extensions.Configuration" Version="8.0.0" />
     <PackageReference Include="Microsoft.Extensions.Configuration.Json" Version="8.0.1" />
     </ItemGroup>

     <ItemGroup>
       <None Update="appsettings.json">
         <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
        </None>
     </ItemGroup>

    </Project>
    ```    

     ![](../media/l5-12-101.png)    

1. Navigate to the folder for your preferred language and install the necessary packages.

     **C#:**

    ```
    export DOTNET_ROOT=$HOME/.dotnet
    export PATH=$DOTNET_ROOT:$PATH
    mkdir -p $DOTNET_ROOT
    ```     

     >**Note:** Azure Cloud Shell often does not have admin privileges, so you need to install .NET in your home directory. So here you are creating a separate `.dotnet` directory under your home directory to isolate your configuration.
     - `DOTNET_ROOT` specifies where your .NET runtime and SDK are located (in your `$HOME/.dotnet directory`).
     - `PATH=$DOTNET_ROOT:$PATH` ensures that the locally installed .NET SDK can be accessed globally by your terminal.
     - `mkdir -p $DOTNET_ROOT` This creates the directory where the .NET runtime and SDK will be installed.

1. Run the following command to install the required SDK version locally:     

     ```
     wget https://dotnet.microsoft.com/download/dotnet/scripts/v1/dotnet-install.sh
     chmod +x dotnet-install.sh
     ./dotnet-install.sh --version 8.0.404 --install-dir $DOTNET_ROOT
     ```

      >**Note:** These commands download and prepare the official `.NET` installation script, grant it execute permissions, and install the required .NET SDK version (8.0.404) in the `$DOTNET_ROOT` directory, as we don't have the admin privileges to install it globally.
      
      >**Note:** If the commands do not execute as a bunch, kindly run them one by one.

1. Enter the following command to restore the workload.

    ```
    dotnet workload restore
    ```

     >**Note:** Restores any required workloads for your project, such as additional tools or libraries that are part of the .NET SDK.
    
1. Enter the following command to add the `Azure.AI.OpenAI` NuGet package to your project, which is necessary for integrating with Azure OpenAI services.

    ```
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.14
    ```

1. For Python, run the following command to install the dependencies

    **Python**

    ```bash
   pip install requests
    ```
      > **Note:** If you receive a permission error after executing the pip install command, please use the below command to install.
      > ```
      > pip install --user requests
      > ```

### Task 3.3: View application code

In this task, you will explore the code used to call the REST API and generate an image.

1. In the code editor pane, select the main code file for your application:

    - C#: `Program.cs`
    - Python: `generate-image.py`

2. Review the code that the file contains, noting the following key features:

   >**Note:** Right-click on the file from the left pane, and hit **Save**
   
    - The code makes HTTPS requests to the endpoint for your service, including the key for your service in the header. Both of these values are obtained from the configuration file.
    - The process consists of <u>two</u> REST requests: One to initiate the image-generation request, and another to retrieve the results.
    The initial request includes the following data:
        - The user-provided prompt that describes the image to be generated
        - The number of images to be generated (in this case, 1)
        - The resolution (size) of the image to be generated.
    - The response header from the initial request includes an **operation-location** value that is used for the subsequent callback to get the results.
    - The code polls the callback URL until the status of the image-generation task is *succeeded*, and then extracts and displays a URL for the generated image.

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="46dc5a95-0801-4085-b021-c775e7b1b06b" />

## Task 4: Run the app 

In this task, you will run the reviewed code to generate some images.

1. In the Cloud Shell bash terminal, navigate to the folder for your preferred language.

1. In the console prompt pane, enter the appropriate command to run your application:

    **C#**

    ```bash
   dotnet run
    ```

    **Python**

    ```bash
    python generate-image.py
    ```
    
1. In the **terminal**, when prompted with **Enter a prompt to request an image**, type the prompt **“A giraffe flying a kite” (1)** and press **Enter**.  Once the request is processed, the generated image file will be saved automatically, and the **file path of the generated image (2)** will be displayed.

    - **Python :**

         ![](../media/Dallpy.png)   

    - **C# :**

         ![](../media/DallCS01.png)

1. Copy the **file path (1)**, then click on the **upload/download (2)** option, and click on **download (3)**.

   ![](../media/model-3.png)

1. In the **Download a file** window, enter the generated file path **(4)** and click **Download (5)** to download the image file to your system.

    ![](../media/Dall11.png)

1. After the download begins, click **Click here to download your file (6)** to open the downloaded image from the browser.

    ![](../media/Dall12.png)  

1. In the **browser Downloads panel**, locate the downloaded file and click **Open file (7)** to view the generated image.

    ![](../media/Dall13.png)  

1. The generated image will open in the viewer, displaying the result based on the prompt **“A giraffe flying a kite.”**

    ![](../media/Dall15.png)  

## Summary

In this lab, you have accomplished the following:
-   Understand the concepts of image generation via the  model.
-   Implement image generation into your applications using this model

### You have successfully completed the lab.
