---
title: 以系統管理員身分執行
ms.date: 06/05/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d012c0902aa82eb057f9d69c0b85b13262e847a
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66747615"
---
# <a name="user-permissions-and-visual-studio"></a>使用者權限和 Visual Studio

基於安全性原因，您最好盡可能以一般使用者身分來執行 Visual Studio。

> [!WARNING]
> 您也應該確保不會編譯、啟動或偵錯任何不是來自受信任者或受信任位置的 Visual Studio 方案。

您可以用一般使用者身分在 Visual Studio IDE 中執行幾乎所有操作。 您需要有系統管理員權限才能完成下列工作：

|區域圖|工作|如需詳細資訊|
|----------|----------| - |
|安裝|安裝 Visual Studio。|[安裝 Visual Studio](../install/install-visual-studio.md)|
||安裝、更新或移除本機說明內容。|[安裝和管理本機說明內容](../help-viewer/install-manage-local-content.md)|
|工具箱|將傳統 COM 控制項新增至 [工具箱]  。|[工具箱](../ide/reference/toolbox.md)|
|建置|使用註冊元件的建置後事件。|[了解自訂建置步驟和建置事件](/cpp/build/understanding-custom-build-steps-and-build-events)|
||包含當您建置 C++ 專案時的註冊步驟。||
|偵錯|對以更高權限執行的應用程式進行偵錯。|[偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)|
||對在不同使用者帳戶下執行的應用程式進行偵錯，例如 ASP.NET 網站。|[對 ASP.NET 和 AJAX 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||在 XAML 瀏覽器應用程式 (XBAP) 的區域中進行偵錯。|[WPF 主應用程式 (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||使用模擬器來對 Microsoft Azure 雲端服務專案進行偵錯。|[在 Visual Studio 中針對雲端服務進行偵錯](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||設定遠端偵錯的防火牆。|[遠端偵錯](../debugger/remote-debugging.md)|
|效能工具|對應用程式進行程式碼剖析。|[效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)|
|部署|將 Web 應用程式部署到本機電腦上的 Internet Information Services (IIS)。|[使用 Visual Studio 部署 ASP.NET Web 應用程式](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>以系統管理員身分執行 Visual Studio

如果您需要以系統管理員身分執行 Visual Studio，請遵循下列步驟來開啟 IDE：

> [!NOTE]
> 這些指示適用於 Windows 10。 其他 Windows 版本的指示與這些相似。

::: moniker range="vs-2017"

1. 開啟 [開始]  功能表，然後捲動至 Visual Studio 2017。

1. 從 **Visual Studio 2017** 的操作功能表 (按一下滑鼠右鍵)，選取 [更多]  >[以系統管理員身分執行]  。

   在 Visual Studio 啟動時， **(系統管理員)** 會顯示在標題列的產品名稱之後。

::: moniker-end

::: moniker range=">=vs-2019"

1. 開啟 [開始]  功能表，然後捲動至 Visual Studio 2019。

1. 從 **Visual Studio 2019** 的操作功能表 (按一下滑鼠右鍵)，選取 [更多]  >[以系統管理員身分執行]  。

   在 Visual Studio 啟動時， **(系統管理員)** 會顯示在標題列的產品名稱之後。

::: moniker-end

您也可以將應用程式捷徑修改為一律以系統管理權限執行。

## <a name="see-also"></a>另請參閱

- [移植、移轉及升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [安裝 Visual Studio](../install/install-visual-studio.md)