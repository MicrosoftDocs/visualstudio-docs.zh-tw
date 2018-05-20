---
title: Azure Functions 簡介
description: 在 Visual Studio for Mac 使用 Azure 函式。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="introduction-to-azure-functions"></a>Azure Functions 簡介

Azure 函式是一種不必明確佈建或管理基礎結構，就能在雲端建立和執行事件驅動程式碼片段 (函式) 的方法。 如需 Azure Functions 的詳細資訊，請參閱 [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions/)。

## <a name="requirements"></a>需求

Azure 函式工具隨附於 **Visual Studio for Mac 7.5**。

若要建立和部署函式，您還需要 Azure 訂用帳戶，這可從 [https://azure.com/free](https://azure.com/free) 免費取得。

## <a name="creating-your-first-azure-functions-project"></a>建立您的第一個 Azure Functions 專案

1. 在 Visual Studio for Mac，選擇 [檔案] > [新增解決方案...] 
2. 從 [新增專案] 對話方塊，選取 [雲端] > [一般] 下的 Azure Functions 範本，然後按一下 [下一步]：

    ![顯示 Azure 函式選項的 [新增專案] 對話方塊](media/azure-functions-image1.png)

3. 輸入**專案名稱**，然後選取 [建立]。

Visual Studio for Mac 會建立一個 .NET Standard 專案，其中包含預設 HttpTrigger 函式。 其中也包含多種 **AzureWebJobs** 套件以及 **Newtonsoft.Json** 套件的 NuGet 參考。

![Visual Studio for Mac 編輯器顯示來自範本的全新 Azure 函式](media/azure-functions-newproj.png)

新的專案會包含下列檔案：

* **HttpTrigger.cs** - 此類別包含 HTTP 觸發函式的重複使用程式碼。 其中包含具有函式名稱的 **FunctionName** 屬性，以及會指定由 HTTP 要求觸發函式的觸發程序屬性 **HttpTrigger**。 如需函式方法的詳細資訊，請參閱 [Azure Functions C# 開發人員參考](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library)文章。
* **host.json** - 此檔案描述 Functions 主機的全域設定選項。 如需範例檔案以及此檔案的可用設定相關資訊，請參閱 [Azure Functions 的 host.json 參考](https://docs.microsoft.com/azure/azure-functions/functions-host-json)。
* **local.settings.json** - 此檔案包含用於在本機執行函式的所有設定。 Azure Functions Core Tools 會使用這些設定。 如需詳細資訊，請參閱 Azure Functions Core Tools 文章中的[本機設定檔](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file)。

現在您已在 Visual Studio for Mac 建立了新的 Azure Functions 專案，因此可從本機電腦試用預設 HTTP 觸發函式。

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>在本機測試函式

透過 Visual Studio for Mac 中的 Azure Functions 支援，您可以在本機開發電腦上測試函式並對其偵錯。

1. 若要在本機測試您的函式，請按 Visual Studio for Mac 中的**執行**按鈕：

    ![Visual Studio for Mac 中的開始偵錯按鈕](media/azure-functions-run.png)

1. 執行專案即開始對 Azure 函式進行本機偵錯，並會開啟新的終端機視窗，如下圖所示： 

    ![顯示函式輸出的終端機視窗](media/azure-functions-terminal.png) 

    請從輸出中複製 URL。

3. 將 HTTP 要求的 URL 貼到您的瀏覽器位址列。 在 URL 結尾新增查詢字串 `?name=<yourname>`，然後執行要求。 下圖顯示函式傳回瀏覽器中對本機 GET 要求的回應：

    ![瀏覽器中的 http 要求](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>建立新函式

函式範本讓您能夠使用最常見的觸發程序和範本快速建立新函式。 當新的Azure Functions 專案建立時，就會自動包含 HttpTrigger 函式。 若要建立其他類型的函式，請執行下方作業：

1. 以滑鼠右鍵按一下 **HttpTrigger.cs** 檔案，然後選取 [移除] 予以移除。 從下方警示選取 [刪除]，將其從您的專案中移除：

    ![從專案移除檔案的對話方塊](media/azure-functions-remove.png)

2. 若要新增函式，請在專案名稱按一下滑鼠右鍵，然後選取 [新增] > [新增函式...]：

    ![新增函式的內容動作](media/azure-functions-addnew.png)

3. 從 [新增 Azure 函式] 對話方塊選取您要的函式：

    ![新增 Azure 函式對話方塊](media/azure-functions-newfunction.png)

    下一節提供 Azure 函式範本的清單。

## <a name="available-function-templates"></a>可用的函式範本

- **HTTP** - 使用 HTTP 要求來觸發程式碼執行。 下列 HTTP 觸發程序有明確的範本：
    - Http GET CRUD
    - Http POST CRUD
    - 含有參數的 Http 觸發程序
    - Http 觸發程序
- **計時器** - 依預先定義的排程執行清理或其他批次工作。 這個範本採用兩個欄位：名稱和排程，即六個欄位的 CRON 運算式。 如需詳細資訊，請參閱[有關時間的 Azure 函式文章](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function)
- **GitHub 觸發程序** - 回應您的 GitHub 存放庫中發生的事件。 如需詳細資訊，請參閱[有關 GitHub 的 Azure Functions 文章](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - GitHub 註解工具 - 這個函式會在收到問題或提取要求的 GitHub Webhook 時執行，並新增註解。
    - GitHub WebHook - 這個函式會在收到 GitHub Webhook 時執行
- **Blob 觸發程序** - 在 Azure 儲存體 Blob 新增到容器時加以處理。 除了函式名稱之外，這個範本也接受路徑和連線屬性。 路徑屬性是觸發程序會監視的儲存體帳戶內部路徑。 連線帳戶是包含儲存體帳戶連接字串的應用程式設定名稱。 如需詳細資訊，請參閱 [Azure 函式 Blob 儲存體文章](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function)。
- **佇列觸發程序** - 這是會在訊息抵達 Azure 儲存體佇列時予以回應的函式。 除了函式名稱之外，這個範本也接受**路徑** (會從中讀取訊息的佇列名稱) 和儲存體帳戶**連線** (包含儲存體帳戶連接字串的應用程式設定名稱)。 如需詳細資訊，請參閱[有關佇列儲存體的 Azure 函式文章](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function)。
- **泛型 WebHook** - 這個簡單函式會在每次從支援 Webhook 的任何服務收到要求時執行。 如需詳細資訊，請參閱[有關泛型 WebHook 的 Azure 函式文章](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function)
- **影像大小調整工具** - 每當有 Blob 新增到容器時，這個函式都會建立調整過大小的影像。 這個範本接受路徑和連接字串、小型影像輸出及中型影像輸出。
- **SAS 權杖** - 這個函式會為指定的 Azure 儲存體容器和 Blob 名稱產生 SAS 權杖。 除了函式名稱之外，這個範本也接受路徑和連線屬性。 路徑屬性是觸發程序會監視的儲存體帳戶內部路徑。 連線帳戶是包含儲存體帳戶連接字串的應用程式設定名稱。 **存取權限**也需要設定。 授權等級會控制是否函式需要 API 金鑰，以及使用哪一個金鑰；函式會使用函式金鑰；管理員則使用您的主要金鑰。 如需詳細資訊，請參閱 [C# Azure Function for generating SAS tokens](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) (用於產生 SAS 權杖的 C# Azure 函式) 樣本。
- **Durable Functions 協調流程** - Durable Functions 可讓您在無伺服器環境中撰寫具狀態函式。 此延伸模組會為您管理狀態、檢查點及重新啟動。 如需詳細資訊，請參閱關於 [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview) 的 Azure 函式指南