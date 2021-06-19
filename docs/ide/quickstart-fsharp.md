---
title: 快速入門：以 F# 建立 ASP.NET Core Web 服務
description: 了解如何在 Visual Studio 中以 F# 逐步建立 ASP.NET Core Web 服務。
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: vs-acquisition
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 298b55120a5e4d0efea1ec5eeeacc2dfa3da274f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386432"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>快速入門：使用 Visual Studio 在 F 中建立您的第一個 ASP.NET Core web 服務\#

在 Visual Studio 中 F# 的這個 5-10 分鐘簡介中，您將建立 F# ASP.NET Core Web 應用程式。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2022"

如果您尚未安裝 Visual Studio 2022 Preview，請前往 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022) 頁面，免費進行安裝。

::: moniker-end

## <a name="create-a-project"></a>建立專案

首先，您將建立 ASP.NET Core Web API 專案。 在新增任何項目之前，專案類型隨附的範本檔案可構成功能性 Web 服務！

::: moniker range="vs-2017"

1. 開啟 Visual Studio。

2. 從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

3. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual F#]，然後選擇 [Web]。 在中間窗格中，選擇 [ASP.NET Web 應用程式]，然後選擇 [確定]。

     如果您看不到 [.NET Core] 專案範本類別，請選擇左窗格中的 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

     ![VS 安裝程式中的 ASP.NET 工作負載](../ide/media/quickstart-aspnet-workload.png)

4. 在 [新增 ASP.NET Core Web 應用程式] 對話方塊中，從上方的下拉式功能表中選取 [ASP.NET Core 2.1]  (如果您在清單中看不到 **ASP.NET Core 2.1** ，請遵循應該出現在接近對話方塊頂端之黃色列中的 **下載** 連結進行安裝。 ) 選擇 **[確定]**。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 Visual Studio。

2. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

3. 在 [建立新專案] 頁面上，於搜尋方塊中輸入 **f# web**，然後選擇 [ASP.NET Core Web 應用程式] 專案範本。 選擇 [下一步]。

4. 在 [設定新專案] 頁面上輸入名稱，然後選擇 [建立]。

5. 在 [建立新的 ASP.NET Core Web 應用程式] 頁面上，從上方的下拉式功能表中選取 [ASP.NET Core 2.1]，然後選擇 [建立]。

::: moniker-end

## <a name="explore-the-ide"></a>探索 IDE

1. 在方案總管工具列中，展開 [Controllers] 資料夾，然後選擇 [ValuesController.fs] 以在編輯器中予以開啟。

   ![F# Web API 專案中展開 Controllers 資料夾的方案總管](../ide/media/hello-world-fs-sln-explorer.png)

2. 接下來，將 `Get()` 成員修改如下：

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

程式碼十分簡單。 F# 值陣列繫結至 `values` 名稱，然後傳遞至 ASP.NET Core MVC 架構作為 `ActionResult`。 ASP.NET Core 會負責為您處理其餘作業。

它在編輯器中應該看起來如下：

![已修改的 Get 成員](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>執行應用程式

1. 按下 **Ctrl** + **F5** 執行應用程式，並在網頁瀏覽器中開啟它。

2. 此頁面應該瀏覽至 `/api/values` 路由，但如果不存在，則請將 `https://localhost:44396/api/values` 輸入瀏覽器中。

網頁瀏覽器現在會顯示符合您先前鍵入內容的 JSON。

## <a name="next-steps"></a>後續步驟

恭喜您完成此快速入門！ 我們希望您更了解 F#、ASP.NET Core 和 Visual Studio IDE。 若要查看公用伺服器上執行的應用程式，請選取下列按鈕。

> [!div class="nextstepaction"]
> [將應用程式部署至 Azure App Service](../deployment/quickstart-deploy-to-azure.md)

若要深入了解 F#，請參閱正式 [F# 指南](/dotnet/fsharp/index)。
