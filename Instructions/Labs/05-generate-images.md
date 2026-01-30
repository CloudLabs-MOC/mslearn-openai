# Lab: Generate images with a DALL-E model

## Estimated Duration: 45 Minutes

## Lab Overview

In this lab, you'll use a DALL-E version 3 model to generate images based on natural language prompts.

The Azure OpenAI Service includes an image-generation model named DALL-E. You can use this model to submit natural language prompts that describe a desired image, and the model will generate an original image based on the description you provide.

## Lab Objectives

In this lab, you will complete the following tasks:

- Task 1: Provision an Azure OpenAI resource
- Task 2: Explore image-generation in the DALL-E playground
- Task 3: Use the REST API to generate images
- Task 3.1: Prepare the app environment
- Task 3.2: Configure your application
- Task 3.3: View application code
- Task 4: Run the app

### Task 1:  Provision an Azure OpenAI resource

In this task , you'll create an Azure resource in the Azure portal, selecting the OpenAI service and configuring settings such as region and pricing tier. This setup allows you to integrate OpenAI's advanced language models into your applications.

1. In the **[Azure portal](https://portal.azure.com/)**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)**.

      ![](../media/l1-12-0.png)

2. On the **Microsoft Foundry | Azure OpenAI** page, select **Azure OpenAI (1)** from the left pane, click **+ Create (2)** drop-down and click on **Azure OpenAI (3)**.

     ![](../media/va1.png)

3. Create an **Azure OpenAI** resource with the following settings, click on **Next (6)** thrice and subsequently click on **Create**:
   
      - **Subscription**: Default - Pre-assigned subscription. **(1)**
      - **Resource group**: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
      - **Region**: Select **<inject key="Region" enableCopy="false" /> (3)**
      - **Name**: **OpenAI-Lab06-<inject key="DeploymentID" enableCopy="false"></inject> (4)**
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

<validation step="cafb7718-6bf1-4fe9-88b8-d1ed6d7c4c58" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

## Task 2: Explore image generation in the DALL-E playground

In this task, you will use the DALL-E playground in the Microsoft Foundry portal to experiment with image generation.

> **Note:** This task relies on the DALL·E quota limit available in your Azure OpenAI resource. If the deployment fails, it may be due to quota restrictions on the existing resource. 

> To resolve this, create a new Azure OpenAI resource in a supported region such as **East US** or **Australia East**, and then attempt to deploy the DALL·E model again.

1. In the **Azure portal**, search for **Azure OpenAI (1)** and select **Azure OpenAI (2)**.

      ![](../media/l1-12-0.png)

2. On the **Microsoft Foundry | Azure OpenAI** page, ensure that **Azure OpenAI (1)** is selected from the left blade. Then, select **OpenAI-Lab06-<inject key="DeploymentID" enableCopy="false"></inject>(2)**

      ![](../media/l5-12-1.png)

3. In the Azure OpenAI resource pane, click on **Go to Foundry portal**, which will navigate to the **Microsoft Foundry portal**.

      ![](../media/l5-12-2.png)

4. On the **Microsoft Foundry portal** page, select **Deployments (1)** under **Shared Resources** from the left pane. Then, click **+ Deploy Model (2)** and choose **Deploy Base Model (3)**.

      ![](../media/l5-12-3.png)

5. In the **Select a model** page, search for **dall-e-3 (1)**, select **dall-e-3 (Text to image) (2)** model, and click on **Confirm (3)**

      ![](../media/l5-12-4.png)

6. Within the **Deploy model** pop-up interface, enter the **Deployment name** as **Dalle3 (1)**, Click on **Customize (2)** and make the **Requests per Minute Rate Limit: 3 (3)** and click on **Deploy (4)**.

      ![](../media/l5-12-5.png)

      ![](../media/l5-12-6.png)
              
4. From the left navigation pane, select **Images (1)**, enter a description of an image you'd like to generate in the **Describe the image you want to generate (2)** box (for example, `An elephant on a skateboard`), and then select **Generate (3)** to view the **resulting image (4)**.
   
      ![The DALL-E Playground in Azure OpenAI Studio with a generated image.](../media/l5-12-7.png)

5. Modify the prompt to provide a more specific description. For example, `An elephant on a skateboard in the style of Picasso`. Then generate the new image and review the results.

      ![The DALL-E Playground in Azure OpenAI Studio with two generated images.](../media/l5-12-8.png)

      > **Note:** The image may appear differently than shown in the screenshot. 

## Task 3: Use the REST API to generate images 

The Azure OpenAI service provides a REST API that you can use to submit prompts for content generation, including images generated by a DALL-E model.

### Task 3.1: Prepare the app environment

In this task, you will use a simple Python or C# app to generate images by calling the REST API and running the code in the Cloud Shell console interface within the Azure portal.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/cloudshell-launch-portal.png#lightbox)

    > **Note:** If a **Cloud Shell timed out** pop-up appears, click **Reconnect**.

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **Bash**. If you don't see this option, skip the step.

     ![](../media/bash.png)

1. Within the **Getting started** page, select **Mount storage account (1)**, select your **Subscription (2)** from the dropdown and click **Apply (3)**.

     ![](../media/mountstrg.png)

1. On the **Mount storage account** screen, select **I want to create a storage account (1)** and click on **Next (2)**.

    ![](../media/csanext.png)

1. Provide the following details:

    - **Subscription**: Default - Pre-assigned subscription **(1)**.
    - **Resource group**: **openai-<inject key="DeploymentID" enableCopy="false"></inject> (2)**
    - **Region**: Select **<inject key="Region" enableCopy="false" /> (3)**
    - **Storage account name**: **stg<inject key="DeploymentID" enableCopy="false"></inject> (4)**
    - **File share**: none **(5)**
    - Click **Create (6)**

      ![](../media/l5-12-st.png)
    
1. Once the terminal opens, click on **Settings** and select **Go to Classic Version**.

   ![](../media/classic-cloudshell.png)

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

    ![](../media/l5-12-9.png)

### Task 3.2: Configure your application

In this task, you will use a configuration file in the application to store the details needed to connect to your Azure OpenAI service account.

1. In the code editor, select the configuration file for your app, depending on your language preference.

    - C#: `appsettings.json`
    - Python: `.env`
    
2. Update the configuration values to include the **Endpoint**, **Key1** and **Deployment name: Dalle3** for your Azure OpenAI service. Then, save the file by right-clicking the file in the left pane.

    > **Tip:** You can adjust the split at the top of the cloud shell pane to see the Azure portal and get the endpoint and key values from the **Keys and Endpoint** page for your Azure OpenAI service.

3. If you are using **Python**, you'll also need to install the **python-dotenv** package used to read the configuration file. In the console prompt pane, ensure the current folder is **~/azure-openai/Labfiles/05-image-generation/Python**. Then enter this command:

    ```bash
   pip install python-dotenv
    ```
      > **Note:** If you receive a permission error after executing the installation command as shown in the image, please run the command below for installation/
      >    ![](../media/L2T3S9python-0205.png)
      > ```bash
      > pip install --user python-dotenv
      > ```

1. If you're using **C#**, navigate to `generate_image.csproj`, delete the existing code, then replace it with the following code and then press **Ctrl+S** to save the file.

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
     <PackageReference Include="Microsoft.Extensions.Configuration" Version="8.0.404" />
     <PackageReference Include="Microsoft.Extensions.Configuration.Json" Version="8.0.404" />
     </ItemGroup>

     <ItemGroup>
       <None Update="appsettings.json">
         <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
        </None>
     </ItemGroup>

    </Project>
    ```    

     ![](../media/l5-12-10.png)    

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
1. When prompted, enter a description for an image. For example, **A giraffe flying a kite**.
    
1. Wait for the image to be generated - a hyperlink will be displayed in the console pane. Then select the hyperlink to open a new browser tab and review the image that was generated.

   ![](../media/l5-12-11.png "Keys and Endpoints")

   ![](../media/dev-genai-june-10.png)

1. Close the tab containing the generated image and re-run the app to generate a new image with a different prompt and once done close the cloudshell.

## Summary

In this lab, you have accomplished the following:
-   Understand the concepts of image generation via the DALL-E model.
-   Implement image generation into your applications using this model

### You have successfully completed the lab.Click Next >> to continue to the next lab.

![Launch Azure Portal](../media/l5-next.png)
