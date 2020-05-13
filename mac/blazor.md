---
title: 創建布拉佐爾網路應用程式
description: 在 Mac 視覺化工作室中提供有關 ASP.NET核心應用中的 Blazor 支援的資訊。
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737583"
---
# <a name="create-blazor-web-apps"></a>創建布拉佐爾網路應用程式

本指南介紹了創建第一個 Blazor Web 應用的介紹。 有關更深入的指導，請參閱[ASP.NET核心布拉佐爾簡介](/aspnet/core/blazor/index)。

適用于 Mac 的視覺化工作室（從 8.4 版開始）包括對開發和發佈核心 Blazor 伺服器應用程式ASP.NET的支援。 Blazor 是一個使用 .NET 構建互動式用戶端 Web UI 的框架，它為 Web 開發人員提供了以下優勢：

* 以 C# 撰寫而不是 JavaScript。
* 利用 .NET 程式庫的現有 .NET 生態系統。
* 跨伺服器和用戶端共用應用程式邏輯。
* 受益于。NET 的性能、可靠性和安全性。
* 借助 PC、Linux 和 macOS 上的視覺化工作室，提高工作效率。
* 以常用的語言、架構和工具建置，不僅穩定、功能豐富，而且容易使用。

## <a name="creating-a-new-blazor-project"></a>創建新的布拉佐爾專案

1. 在 **"開始"視窗中**，選擇 **"新建"** 以創建新專案：

   ![Mac 啟動視窗的視覺化工作室，突出顯示了新選擇](media/blazor-new-project.png)
1. 在 **"新專案**"對話方塊中，選擇 **.NET 核心**>**應用**> **Blazor 伺服器應用**，然後選擇 **"下一步**：![選擇已選擇 Blazor 伺服器應用範本的新專案對話方塊"範本](media/blazor-project-template.png)

1. 選擇 .NET 核心 3.1 作為目標框架，然後選擇 **"下一步**"。 
   ![配置顯示的新 Blazor 伺服器應用對話方塊，並將目標框架選擇為 .NET 核心 3.1](media/blazor-select-target-framework.png)

1. 為專案選擇名稱，如果需要，請添加 Git 支援。 選取 [Create] \(建立\)**** 以建立專案。
   ![B 配置輸入專案名稱時顯示的新 Blazor 伺服器應用對話方塊](media/blazor-name-project.png)

   Mac 視覺化工作室在"代碼"佈局視窗中打開您的專案。
1. 選擇 **"在不** > **調試的情況下運行啟動**"以運行應用。

   視覺工作室啟動[Kestrel，](/aspnet/core/fundamentals/servers/kestrel)打開瀏覽器到`https://localhost:5001`，並顯示您的Blazor網路應用程式。

   ![野生動物園中的布拉佐爾網路應用程式](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Mac 視覺工作室中的布拉佐爾支援

適用于 Mac 的視覺化工作室（從 8.4 版開始）包含新功能，可説明您創建新的 Blazor 伺服器專案。 並且，它還為您提供您期望的標準支援，例如構建、運行和調試 Blazor 專案。 

在上面的演練中，我們看到了 Blazor 伺服器應用程式專案範本如何説明您創建新的 Blazor 伺服器應用專案。 讓我們來看看 Visual Studio 中支援 Blazor 伺服器專案開發的其他功能。

### <a name="editor-support-for-razor-files"></a>編輯支援 *.razor*檔
適用于 Mac 的 Visual Studio 包括支援編輯 .razor 檔 - 創建 Blazor 應用程式時將使用的大多數檔。 IDE 的 Windows 和 Mac 版本共用 .razor 檔的相同編輯器。 您將看到對 .razor 檔的完整著色和完成支援，包括專案中聲明的 Razor 元件的完成情況。

![Mac 編輯器視窗的視覺化工作室，顯示 Blazor 的"無意義"](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>將 Blazor 應用程式發佈到 Azure 應用服務
您還可以將 Blazor 應用程式直接發佈到 Azure 應用服務。 如果沒有 Azure 帳戶在 Azure 上運行 Blazor 應用，則始終可以[在此處註冊免費](https://azure.microsoft.com/free)應用，該帳戶還包括 12 個月的免費熱門服務、200 美元的免費 Azure 積分以及超過 25 個始終免費的服務。

![顯示 Azure 發佈體驗的 Mac 視覺化工作室](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>專案解析

預設情況下，Blazor Web 應用程式包括幾個目錄和檔。 在入門時，您需要熟悉以下主要功能：

### <a name="pages-folder"></a>Pages 資料夾

此資料夾包含專案的網頁，這些網頁使用 *.razor*檔副檔名。

### <a name="shared-folder"></a>共用資料夾

此資料夾包括共用元件，也使用 *.razor*副檔名。 您將看到，這包括*MainLayout.razor*，用於在整個應用程式中定義公共佈局。 它還包括共用的*NavMenu.razor*元件，該元件在所有頁面上使用。 如果要創建可重用的元件，它們將位於 **"共用"** 資料夾中。

### <a name="app-settings"></a>應用程式設定

*appSettings.json*檔包含配置資料，如連接字串。

有關配置的詳細資訊，請參閱 ASP.NET[指南中的配置](/aspnet/core/fundamentals/configuration/index)。

### <a name="wwwroot-folder"></a>wwwroot 資料夾

此資料夾包含靜態檔，如 HTML、JavaScript 和 CSS 檔。 如需詳細資訊，請參閱 [ASP.NET Core 中的靜態檔案](/aspnet/core/fundamentals/static-files)。

### <a name="programcs"></a>Program.cs

此檔包含程式的進入點。 如需詳細資訊，請參閱 [ASP.NET Core Web 主機](/aspnet/core/fundamentals/host/web-host)。

### <a name="startupcs"></a>Startup.cs

此檔包含配置應用行為的代碼，例如應用是否需要 Cookie 的同意。 如需詳細資訊，請參閱 [ASP.NET Core 中的應用程式啟動](/aspnet/core/fundamentals/startup)。

## <a name="summary"></a>摘要
在本教程中，您瞭解了如何在 Visual Studio 中為 Mac 創建新的 Blazor 伺服器應用程式，並瞭解了適用于 Mac 的 Visual Studio 提供的一些功能，以説明您創建 Blazor 應用程式。

## <a name="see-also"></a>另請參閱

有關創建 Blazor Web 應用程式的更全面的指南，請參閱[ASP.NET核心 Blazor 簡介](/aspnet/core/blazor/index)。
