---
title: Azure Functions 簡介
description: 在 Visual Studio for Mac 中使用 Azure Functions。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: 63793548bd3ea1098cc1113724cd9a3b513adbf5
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727459"
---
# <a name="introduction-to-azure-functions"></a>Azure Functions 簡介

Azure 函式是一種不必明確佈建或管理基礎結構，就能在雲端建立和執行事件驅動程式碼片段 (函式) 的方法。 如需 Azure Functions 的詳細資訊，請參閱 [Azure Functions 文件](/azure/azure-functions/)。

## <a name="requirements"></a>規格需求

Azure 函式工具隨附於 **Visual Studio for Mac 7.5**。

若要建立和部署函式，您也需要 Azure 訂用帳戶，您可以從免費取得該訂用帳戶 [https://azure.com/free](https://azure.com/free) 。

## <a name="creating-your-first-azure-functions-project"></a>建立您的第一個 Azure Functions 專案

1. 在 Visual Studio for Mac 中，選取 [檔案] **> [新方案**]。
2. 從 [新增專案] 對話方塊，選取 [雲端] > [一般] 下的 Azure Functions 範本，然後按一下 [下一步]：

    ![顯示 Azure 函式選項的 [新增專案] 對話方塊](media/azure-functions-image1.png)

3. 選取您想要使用的初始 Azure Functions 範本，並輸入您的函數名稱，然後按 [下一步]。

    ![顯示 Azure Functions 範本的 [新增專案] 對話方塊](media/azure-functions-image2.png)

    根據您選取的函數類型，下一頁將會提示您鍵入詳細資料 (例如存取權限)，如下圖所示：

    ![顯示其他選項的 [新增專案] 對話方塊](media/azure-functions-image3.png)

    如需不同類型之 Azure Functions 範本以及設定每個範本所需之繫結屬性的詳細資訊，請參閱[可用函數範本](#available-function-templates)一節。 在此範例中，我們將使用存取權限設為匿名的 Http 觸發程序。

4. 在您設定參數之後，請選擇專案的位置，然後按一下 [建立]。

Visual Studio for Mac 會建立包含預設函數的 .NET Standard 專案。 其中也包含多種 **AzureWebJobs** 套件以及 **Newtonsoft.Json** 套件的 NuGet 參考。

![Visual Studio for Mac 編輯器顯示來自範本的全新 Azure 函式](media/azure-functions-newproj.png)

新專案包含下列檔案：

* **your-function-name.cs** – 此類別包含您所選取函數的未定案程式碼。 其中包含具有函數名稱的 **FunctionName** 屬性，以及指定觸發函數項目的觸發程序屬性 (例如 HTTP 要求)。 如需函式方法的詳細資訊，請參閱 [Azure Functions C# 開發人員參考](/azure/azure-functions/functions-dotnet-class-library)文章。
* **host.json** - 此檔案描述 Functions 主機的全域設定選項。 如需範例檔案以及此檔案的可用設定相關資訊，請參閱 [Azure Functions 的 host.json 參考](/azure/azure-functions/functions-host-json)。
* **local.settings.json** - 此檔案包含用於在本機執行函式的所有設定。 Azure Functions Core Tools 會使用這些設定。 如需詳細資訊，請參閱＜Azure Functions Core Tools＞一文中的[本機設定檔](/azure/azure-functions/functions-run-local#local-settings-file)。

現在您已在 Visual Studio for Mac 建立了新的 Azure Functions 專案，因此可從本機電腦試用預設 HTTP 觸發函式。

## <a name="testing-the-function-locally"></a>在本機測試函式

透過 Visual Studio for Mac 中的 Azure Functions 支援，您可以在本機開發電腦上測試函式並對其偵錯。

1. 若要在本機測試您的函式，請按 Visual Studio for Mac 中的 **執行** 按鈕：

    ![Visual Studio for Mac 中的開始偵錯按鈕](media/azure-functions-run.png)

1. 執行專案即開始對 Azure 函式進行本機偵錯，並會開啟新的終端機視窗，如下圖所示：

    ![顯示函式輸出的終端機視窗](media/azure-functions-terminal.png)

    請從輸出中複製 URL。

3. 將 HTTP 要求的 URL 貼到瀏覽器的網址列。 在 URL 結尾新增查詢字串 `?name=<yourname>`，然後執行要求。 下圖顯示函式傳回瀏覽器中對本機 GET 要求的回應：

    ![瀏覽器中的 http 要求](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>將另一個函數新增至專案

函式範本讓您能夠使用最常見的觸發程序和範本快速建立新函式。 若要建立其他類型的函式，請執行下方作業：

1. 若要新增函式，請在專案名稱按一下滑鼠右鍵，然後選取 [新增] > [新增函式...]：

    ![新增函式的內容動作](media/azure-functions-addnew.png)

2. 從 [新增 Azure 函式] 對話方塊選取您要的函式：

    ![新增 Azure 函式對話方塊](media/azure-functions-image4.png)

    [可用函數範本](#available-function-templates)一節提供 Azure 函數範本的清單。

您可以使用上述程序，對函式應用程式專案新增更多函式。 專案中的每個函式都可以有不同的觸發程序，但函式必須只有一個觸發程序。 如需詳細資訊，請參閱 [Azure Functions 觸發程式和](/azure/azure-functions/functions-triggers-bindings)系結概念。

## <a name="publish-to-azure"></a>發佈至 Azure

1. 以滑鼠右鍵按一下專案名稱，然後選取 [ **發行] > 發佈至 Azure**：  ![ Azure Functions 的螢幕擷取畫面，其中顯示已選取的 AF HTTPtrigger 專案，以及在內容功能表中反白顯示的 [發佈和發佈至 azure] 命令。](media/azure-functions-image5.png)
2. 如果您已將 Azure 帳戶連線至 Visual  Studio for Mac，則會顯示可用的應用程式服務清單。 如果您尚未登入，則系統會提示您這麼做。
3. 從 [Publish to Azure App Service] \(發行至 Azure App Service\) 對話方塊中，您可以選取現有應用程式服務，或按一下 [新增] 來建立新的應用程式服務。
4. 在 [ **建立新的 App Service** ] 對話方塊中，輸入您的設定：  ![ Azure Functions 中新的 App Service 視窗的螢幕擷取畫面，其中顯示在 Azure 上建立新 App Service 的設定。](media/azure-functions-image7.png)

    |設定  |描述  |
    |---------|---------|
    |**App Service 名稱**|識別新函數應用程式的全域唯一名稱。|
    |**訂用帳戶**|要使用的 Azure 訂用帳戶。|
    |**[資源群組](/azure/azure-resource-manager/resource-group-overview)**|要在其中建立函式應用程式的資源群組名稱。 選擇 **+** 建立新的資源群組。|
    |**[服務方案](/azure/azure-functions/functions-scale)**|選擇現有方案，或建立自訂方案。 選擇區域中接近您或接近您函數所存取之其他服務的位置。|

    > [!CAUTION]
    > Visual Studio for Mac 7.6 版中有一個 Bug，如果您嘗試建立 [定價] 設定為 [使用] 的自訂服務方案，則會導致包含佈建錯誤的發行失敗。 下一個服務版本會修正此問題。

5. 按 [下一步] 來建立儲存體帳戶。 Functions 執行階段需要 Azure 儲存體帳戶。 按一下 [自訂] 來建立一般用途儲存體帳戶，或使用現有儲存體帳戶：

    ![Azure Functions 中 [設定儲存體帳戶] 畫面的螢幕擷取畫面。 系統會為儲存體帳戶選取 [自訂]，並填入 [帳戶名稱] 和 [帳戶類型]。](media/azure-functions-image8.png)

6. 按一下 [建立] 以在 Azure 中使用這些設定建立函式應用程式和相關資源，並且部署函式專案程式碼。

7. 系統可能會在發行期間使用對話方塊提示您，通知您「更新 Azure 上的函數版本」。 按一下 **[是]**：

    ![Azure 對話方塊提示字元之更新函式版本的螢幕擷取畫面，要求您「更新 Azure 應用程式設定以符合區域功能版本」。](media/azure-functions-image12.png)

> [!CAUTION]
> Visual Studio for Mac 7.6 版中有 `FUNCTIONS_EXTENSION_VERSION` 未正確設定為 "beta" 的 Bug，表示您的函數可能未執行。 若要修正此問題，請前往您的[函數應用程式設定](#function-app-settings)，並將 `FUNCTIONS_EXTENSION_VERSION` 從 "-1" 設定為 "beta"。

## <a name="function-app-settings"></a>函數應用程式設定

您在 local.settings.json 中所新增的所有設定，也必須新增至 Azure 中的函式應用程式。 當您發行專案時，不會自動上傳這些設定。

若要存取您的應用程式設定，請前往 azure 入口網站 [https://ms.portal.azure.com/](https://ms.portal.azure.com/) 。 在 [函數應用程式] 下，選取 [函數應用程式]，並反白顯示您的函數名稱：

![Azure 函數功能表](media/azure-functions-image9.png)

從 [概觀] 索引標籤中，選取 [已設定的功能] 下的 [應用程式設定]：

![透過 Azure 函數的索引標籤](media/azure-functions-image10.png)

從這裡，您可以設定函數應用程式的應用程式設定，您可以在其中新增應用程式設定或修改現有應用程式設定：

![Azure 入口網站的應用程式設定區域](media/azure-functions-image11.png)

您可能需要設定的一個重要設定為 `FUNCTIONS_EXTENSION_VERSION`。 從 Visual Studio for Mac 發行時，此值應該設定為 **beta**。

## <a name="available-function-templates"></a>可用的函式範本

- **GitHub 觸發程序** - 回應您的 GitHub 存放庫中發生的事件。 如需詳細資訊，請參閱[有關 GitHub 的 Azure Functions 文章](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub 註解工具 - 這個函式會在收到問題或提取要求的 GitHub Webhook 時執行，並新增註解。
  - GitHub WebHook - 此函數會在收到 GitHub Webhook 時執行。

- **HTTP** - 使用 HTTP 要求來觸發程式碼執行。 下列 HTTP 觸發程序有明確的範本：
  - Http 觸發程序
  - Http GET CRUD
  - Http POST CRUD
  - 含有參數的 Http 觸發程序

- **計時器** - 依預先定義的排程執行清理或其他批次工作。 這個範本採用兩個欄位：名稱和排程，即六個欄位的 CRON 運算式。 如需詳細資訊，請參閱[有關時間的 Azure 函式文章](/azure/azure-functions/functions-create-scheduled-function)

- **佇列觸發程序** - 這是會在訊息抵達 Azure 儲存體佇列時予以回應的函式。 除了函式名稱之外，這個範本也接受 **路徑** (會從中讀取訊息的佇列名稱) 和儲存體帳戶 **連線** (包含儲存體帳戶連接字串的應用程式設定名稱)。 如需詳細資訊，請參閱[有關佇列儲存體的 Azure 函式文章](/azure/azure-functions/functions-create-storage-queue-triggered-function)。

- **Blob 觸發程序** - 在 Azure 儲存體 Blob 新增到容器時加以處理。 除了函式名稱之外，這個範本也接受路徑和連線屬性。 路徑屬性是觸發程序會監視的儲存體帳戶內部路徑。 連線帳戶是包含儲存體帳戶連接字串的應用程式設定名稱。 如需詳細資訊，請參閱 [Azure 函式 Blob 儲存體文章](/azure/azure-functions/functions-create-storage-blob-triggered-function)。

- **泛型 WebHook** - 這個簡單函式會在每次從支援 Webhook 的任何服務收到要求時執行。 如需詳細資訊，請參閱[泛型 Webhook 的 Azure 函數文章](/azure/azure-functions/functions-create-generic-webhook-triggered-function)。

- **Durable Functions 協調流程** - Durable Functions 可讓您在無伺服器環境中撰寫具狀態函式。 此擴充功能會為您管理狀態、設定檢查點和重新啟動。 如需詳細資訊，請參閱 [Durable Functions](/azure/azure-functions/durable-functions-overview) 的 Azure 函數指南。

- **影像大小調整工具** - 每當有 Blob 新增到容器時，這個函式都會建立調整過大小的影像。 這個範本接受路徑和連接字串、小型影像輸出及中型影像輸出。

- **SAS 權杖** - 這個函式會為指定的 Azure 儲存體容器和 Blob 名稱產生 SAS 權杖。 除了函式名稱之外，這個範本也接受路徑和連線屬性。 路徑屬性是觸發程序會監視的儲存體帳戶內部路徑。 連線帳戶是包含儲存體帳戶連接字串的應用程式設定名稱。 **存取權限** 也需要設定。 授權層級可控制函數是否需要 API 金鑰和要使用的金鑰;函數會使用函式金鑰;系統管理員會使用您的帳戶存取金鑰。 如需詳細資訊，請參閱 [C# Azure Function for generating SAS tokens](https://github.com/Azure-Samples/functions-dotnet-sas-token/) (用於產生 SAS 權杖的 C# Azure 函式) 樣本。
