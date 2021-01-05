---
title: 建立 Blazor web 應用程式
description: 提供 Blazor Visual Studio for Mac 中 ASP.NET Core 應用程式支援的相關資訊。
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 30e9a62e8bf0364a76cbd43995cbb77c1a5bd0c4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729414"
---
# <a name="create-no-locblazor-web-apps"></a>建立 Blazor web 應用程式

本指南提供建立第一個 Blazor web 應用程式的簡介。 如需更深入的指引，請參閱[ASP.NET Core Blazor 簡介](/aspnet/core/blazor/index)。

ASP.NET Core Blazor 支援兩種不同的裝載選項; Blazor WebAssembly (WASM) 或 Blazor 伺服器。 Visual Studio for Mac 支援這兩種裝載模型。 Visual Studio for Mac 8.4 + 支援 Blazor Server 和 Visual Studio for Mac 8.6 + 兩者都支援。 如需裝載模型的詳細資訊， Blazor 請參閱 [ASP.NET Core Blazor 裝載模型 ](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1&preserve-view=true)。 您可以在 Blazor WebAssembly Visual Studio for Mac 的預覽 (版本中，透過 **Visual Studio > 檢查更新 ...** 功能表) 中的預覽更新通道，取得在中偵錯工具的支援。

什麼是 Blazor？ Blazor 是使用 .NET 建立互動式用戶端 web UI 的架構，可為 網頁程式開發人員提供下列優點：

* 以 C# 撰寫而不是 JavaScript。
* 利用 .NET 程式庫的現有 .NET 生態系統。
* 跨伺服器和用戶端共用應用程式邏輯。
* 的權益。淨效能、可靠性和安全性。
* 利用 Visual Studio 在 PC、Linux 和 macOS 上保持生產力。
* 以常用的語言、架構和工具建置，不僅穩定、功能豐富，而且容易使用。

## <a name="create-a-new-no-locblazor-webassembly-project"></a>建立新 Blazor WebAssembly 專案
1. 在 [ **開始] 視窗** 中，選取 [ **新增** ] 以建立新的專案：

   ![醒目提示新選項的 Visual Studio for Mac 開始視窗](media/blazor-new-project.png)

1. 在 [**新增專案**] 對話方塊中，選取 [ **.net Core** > **應用** > **Blazor WebAssembly 程式**]，然後選取 [**下一步**]： [ ![ 新增專案] 對話方塊的螢幕擷取畫面，其中會在 [應用程式] 窗格的 [ASP.NET Core] 和 [下一個] 按鈕下反白顯示 [新增專案] 對話方塊 (：： Blazor WebAssembly) ：：](media/blazor-wasm-project-template.png)

1. 選取 [.NET Core 3.1] 作為目標 framework，然後選取 **[下一步]**。 
   ![設定您的新：：：非 loc (Blazor WebAssembly) ：：：應用程式對話方塊，該對話方塊會顯示為已選取為 .NET Core 3.1 的目標 Framework](media/blazor-wasm-select-target-framework.png)

1. 選擇專案的名稱，並視需要新增 Git 支援。 選取 [Create] \(建立\)  以建立專案。
    ![在輸入專案名稱時，會顯示新的：：：非 loc (Blazor WebAssembly) ：：： App 對話方塊](media/blazor-wasm-name-project.png)

   Visual Studio for Mac 會在程式碼配置視窗中開啟您的專案。

1. 選取 [**執行**  >  **啟動但不進行調試** 程式] 以執行應用程式。

   Visual Studio 開始 [Kestrel](/aspnet/core/fundamentals/servers/kestrel)、將瀏覽器開啟至 `https://localhost:5001` ，並顯示您的 Blazor web 應用程式。

   ![：：：非 loc (Blazor) ：：： web 應用程式 Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-no-locblazor-server-project"></a>建立新的 Blazor 伺服器專案

1. 在 [ **開始] 視窗** 中，選取 [ **新增** ] 以建立新的專案：

   ![醒目提示新選項的 Visual Studio for Mac 開始視窗](media/blazor-new-project.png)
1. 在 [**新增專案**] 對話方塊中，選取 [ **.net Core** > **應用** > **Blazor 程式伺服器應用程式**]，然後選取 [**下一步**]： [ ![ 新增專案] 對話方塊的螢幕擷取畫面，並在 [應用程式] 窗格的 [ASP.NET Core] 和 [下一個] 按鈕下反白顯示 [新增專案)  (] 對話方塊。](media/blazor-project-template.png)

1. 選取 [.NET Core 3.1] 作為目標 framework，然後選取 **[下一步]**。 
   ![設定您的新：：：非 loc (Blazor) ：：： Server 應用程式對話方塊，此對話方塊會顯示為已選取為 .NET Core 3.1 的目標 Framework](media/blazor-select-target-framework.png)

1. 選擇專案的名稱，並視需要新增 Git 支援。 選取 [Create] \(建立\)  以建立專案。
   ![當輸入專案名稱時，會顯示新的：：： no-loc (Blazor) ：：： Server 應用程式對話方塊](media/blazor-name-project.png)

   Visual Studio for Mac 會在程式碼配置視窗中開啟您的專案。
1. 選取 [**執行**  >  **啟動但不進行調試** 程式] 以執行應用程式。

   Visual Studio 開始 [Kestrel](/aspnet/core/fundamentals/servers/kestrel)、將瀏覽器開啟至 `https://localhost:5001` ，並顯示您的 Blazor web 應用程式。

   ![：：：非 loc (Blazor) ：：： web 應用程式 Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="no-locblazor-support-in-visual-studio-for-mac"></a>Blazor Visual Studio for Mac 支援

從8.4 版開始的 Visual Studio for Mac () 包含可協助您建立新伺服器專案的新功能 Blazor 。 也提供您預期的標準支援，例如建立、執行和偵測 Blazor 專案。 在 Visual Studio for Mac 8.6 中，已新增建立、建立和執行專案的支援 Blazor WebAssembly 。

在上述的逐步解說中，我們看到 [ Blazor 伺服器應用程式] 專案範本如何協助您建立新的 Blazor 伺服器應用程式或 Blazor WebAssembly 應用程式專案。 讓我們看看 Visual Studio for Mac 中的一些額外功能，以支援 Blazor 專案開發。

### <a name="editor-support-for-razor-files"></a>*Razor* 檔案的編輯器支援
Visual Studio for Mac 包含編輯 razor 檔案的支援，也就是您在建立應用程式時將使用的大部分檔案。 Blazor Visual Studio for Mac 針對您的 razor 檔案（包括專案中所宣告的 Razor 元件的完成）提供完整的顏色標示和完成支援。

![顯示 Intellisense for：：：非 loc (Blazor) ：：：的 Visual Studio for Mac 編輯器視窗](media/blazor-intellisense.png)

### <a name="publishing-no-locblazor-applications-to-azure-app-service"></a>Blazor將應用程式發佈至 Azure App Service
您也可以 Blazor 直接將應用程式發佈至 Azure App Service。 如果您沒有 Azure 帳戶可 Blazor 在 azure 上執行您的應用程式，您可以在 [這裡免費註冊](https://azure.microsoft.com/free) ，這也會隨附12個月免費的熱門服務、$200 的免費 Azure 點數，以及超過25項永遠免費的服務。

![顯示 Azure 發佈體驗的 Visual Studio for Mac](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>專案剖析

Blazor web 應用程式預設會包含幾個目錄和檔案。 當您開始使用時，以下是您需要熟悉的主要專案：

### <a name="pages-folder"></a>Pages 資料夾

此資料夾包含使用 *razor* 副檔名的專案網頁。

### <a name="shared-folder"></a>共用資料夾

此資料夾包含共用元件，也會使用 *razor* 副檔名。 您會看到這包含 *MainLayout*，它是用來定義應用程式之間的一般配置。 它也包含共用的 *NavMenu razor* 元件，用於所有頁面。 如果您要建立可重複使用的元件，這些元件將會移至 **共用** 資料夾。

### <a name="app-settings"></a>應用程式設定

檔案 *appSettings.js* 包含設定資料，例如連接字串。

如需設定的詳細資訊，請參閱 [ASP.NET 指南中](/aspnet/core/fundamentals/configuration/index)的設定。

### <a name="wwwroot-folder"></a>wwwroot 資料夾

此資料夾包含靜態檔案，例如 HTML、JavaScript 和 CSS 檔案。 如需詳細資訊，請參閱 [ASP.NET Core 中的靜態檔案](/aspnet/core/fundamentals/static-files)。

### <a name="programcs"></a>Program.cs

此檔案包含程式的進入點。 如需詳細資訊，請參閱 [ASP.NET Core Web 主機](/aspnet/core/fundamentals/host/web-host)。

### <a name="no-locblazor-server-app-specific-files"></a>Blazor 伺服器應用程式特定檔案
#### <a name="app-settings"></a>應用程式設定

檔案 *appSettings.js* 包含設定資料，例如連接字串。

如需設定的詳細資訊，請參閱 [ASP.NET 指南中](/aspnet/core/fundamentals/configuration/index)的設定。

#### <a name="startupcs"></a>Startup.cs

此檔案包含設定應用程式行為的程式碼，例如應用程式是否需要對 cookie 的同意。 如需詳細資訊，請參閱 [ASP.NET Core 中的應用程式啟動](/aspnet/core/fundamentals/startup)。

## <a name="summary"></a>總結
在本教學課程中，您已瞭解如何 Blazor 在 Visual Studio for Mac 中建立新的伺服器應用程式或 Blazor WebAssembly 應用程式，並瞭解一些 Visual Studio for Mac 提供來協助您建立 Blazor 應用程式的功能。

## <a name="see-also"></a>請參閱

如需建立 Blazor web 應用程式的完整指南，請參閱[ASP.NET Core Blazor 簡介](/aspnet/core/blazor/index)。