---
title: 建立 Blazor web 應用程式
description: 提供 Blazor Visual Studio for Mac 中 ASP.NET Core 應用程式支援的相關資訊。
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 86a8c35d2a379d6afbbe6cf55f53346223e7c462
ms.sourcegitcommit: 5e82a428795749c594f71300ab03a935dc1d523b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86211597"
---
# <a name="create-blazor-web-apps"></a>建立 Blazor web 應用程式

本指南提供建立您的第一個 Blazor web 應用程式的簡介。 如需更深入的指引，請參閱[ASP.NET Core Blazor 簡介](/aspnet/core/blazor/index)。

ASP.NET Core Blazor 支援兩種不同的裝載選項; Blazor伺服器和 Blazor WebAssembly 。 Visual Studio for Mac 支援這兩種裝載模型。 Visual Studio for Mac 8.4 + 支援 Blazor 伺服器和 Visual Studio for Mac 8.6 + 同時支援兩者。 如需裝載模型的詳細資訊， Blazor 請參閱[ASP.NET Core Blazor 裝載模型](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1)。 Visual Studio for Mac 中的偵錯工具支援 Blazor WebAssembly 將于8.6 之後推出。

什麼是 Blazor ？ Blazor是使用 .NET 建立互動式用戶端 web UI 的架構，可為 網頁程式開發人員提供下列優點：

* 以 C# 撰寫而不是 JavaScript。
* 利用 .NET 程式庫的現有 .NET 生態系統。
* 跨伺服器和用戶端共用應用程式邏輯。
* 受益于。NET 的效能、可靠性和安全性。
* 使用電腦、Linux 和 macOS 上的 Visual Studio 保持生產力。
* 以常用的語言、架構和工具建置，不僅穩定、功能豐富，而且容易使用。

## <a name="creating-a-new-blazor-server-project"></a>建立新的 Blazor 伺服器專案

1. 在 [**開始] 視窗**中，選取 [**新增**] 以建立新的專案：

   ![反白顯示新選取範圍的 Visual Studio for Mac 開始視窗](media/blazor-new-project.png)
1. 在 [**新增專案**] 對話方塊中，選取 [ **.net Core** > **應用**程式 > ** Blazor 伺服器應用程式**]，然後選取 **[下一步]**： ![ 選擇已 Blazor 選取伺服器應用程式範本的 [新增專案] 對話方塊的範本](media/blazor-project-template.png)

1. 選取 [.NET Core 3.1] 做為 [目標 framework]，然後選取 **[下一步]**。 
   ![設定新 Blazor 的伺服器應用程式對話方塊，並以選取的目標 Framework 顯示到 .Net Core 3。1](media/blazor-select-target-framework.png)

1. 選擇專案的 [名稱]，並視需要新增 Git 支援。 選取 [Create] \(建立\) 以建立專案。
   ![BConfigure 您在 Blazor 輸入專案名稱時顯示的新伺服器應用程式對話方塊](media/blazor-name-project.png)

   Visual Studio for Mac 會在 [程式碼配置] 視窗中開啟您的專案。
1. 選取 [**執行**]  >  [**啟動但不**進行偵測] 以執行應用程式。

   Visual Studio 啟動[Kestrel](/aspnet/core/fundamentals/servers/kestrel)，將瀏覽器開啟至 `https://localhost:5001` ，並顯示您的 Blazor web 應用程式。

   ![BlazorSafari 中的 web 應用程式](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>BlazorVisual Studio for Mac 中的支援

從8.4 版開始 Visual Studio for Mac () 包含可協助您建立新伺服器專案的新功能 Blazor 。 同樣地，它會提供您預期的標準支援，例如建立、執行和調試 Blazor 專案。 在 Visual Studio for Mac 8.6 中，已加入建立和執行 Blazor WebAssembly 專案的支援。

在上述逐步解說中，我們看到 [ Blazor 伺服器應用程式] 專案範本如何協助您建立新的 Blazor 伺服器應用程式專案。 讓我們看看 Visual Studio for Mac 中的一些額外功能，以支援 Blazor 專案開發。

### <a name="editor-support-for-razor-files"></a>*Razor*檔案的編輯器支援
Visual Studio for Mac 包括編輯 razor 檔案的支援-您在建立應用程式時將使用的大部分檔案 Blazor 。 IDE 的 Windows 和 Mac 版本會共用相同的 razor 檔案編輯器。 您會看到 razor 檔案的完整顏色標示和完成支援，包括專案中所宣告的 Razor 元件完成。

![顯示 Intellisense 的 Visual Studio for Mac 編輯器視窗Blazor](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Blazor將應用程式發佈至 Azure App Service
您也可以 Blazor 直接將應用程式發行至 Azure App Service。 如果您沒有 Azure 帳戶可 Blazor 在 azure 上執行您的應用程式，您隨時都可以在[此註冊免費](https://azure.microsoft.com/free)的免費熱門服務12個月、$200 個免費的 Azure 點數，以及超過25項永遠免費的服務。

![顯示 Azure 發佈經驗的 Visual Studio for Mac](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>專案剖析

Blazorweb apps 預設包含幾個目錄和檔案。 當您開始使用時，以下是您必須熟悉的主要部分：

### <a name="pages-folder"></a>Pages 資料夾

此資料夾包含專案的網頁，其使用*razor*副檔名。

### <a name="shared-folder"></a>共用資料夾

此資料夾包含共用的元件，也會使用*razor*副檔名。 您會看到這包括*MainLayout*，這是用來定義跨應用程式的一般版面配置。 它也包含共用的*navmenu.cshtml razor*元件，用於所有頁面。 如果您要建立可重複使用的元件，它們會進入**共用**資料夾。

### <a name="app-settings"></a>應用程式設定

檔案*上的appSettings.js*包含設定資料，例如連接字串。

如需設定的詳細資訊，請參閱[ASP.NET 中](/aspnet/core/fundamentals/configuration/index)的設定指南。

### <a name="wwwroot-folder"></a>wwwroot 資料夾

此資料夾包含靜態檔案，例如 HTML、JavaScript 和 CSS 檔案。 如需詳細資訊，請參閱 [ASP.NET Core 中的靜態檔案](/aspnet/core/fundamentals/static-files)。

### <a name="programcs"></a>Program.cs

此檔案包含程式的進入點。 如需詳細資訊，請參閱 [ASP.NET Core Web 主機](/aspnet/core/fundamentals/host/web-host)。

### <a name="startupcs"></a>Startup.cs

此檔案包含設定應用程式行為的程式碼，例如應用程式是否需要同意 cookie。 如需詳細資訊，請參閱 [ASP.NET Core 中的應用程式啟動](/aspnet/core/fundamentals/startup)。

## <a name="summary"></a>摘要
在本教學課程中，您已瞭解如何 Blazor 在 Visual Studio for Mac 中建立新的伺服器應用程式，並學習 Visual Studio for Mac 提供來協助您建立應用程式的一些功能 Blazor 。

## <a name="see-also"></a>另請參閱

如需建立 web 應用程式的更完整指南 Blazor ，請參閱[ASP.NET Core Blazor 簡介](/aspnet/core/blazor/index)。
