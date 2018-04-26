---
title: 使用者權限和 Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96835e0f884494f4a6b94aa1a311b40e8a9d8ad9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="user-permissions-and-visual-studio"></a>使用者權限和 Visual Studio

基於安全性原因，您最好盡可能以一般使用者身分來執行 Visual Studio。

> [!WARNING]
> 您也應該確保不會編譯、啟動或偵錯任何不是來自受信任者或受信任位置的 Visual Studio 方案。

身為一般使用者，您可以在 Visual Studio IDE 中執行幾乎所有的作業，但是必須有系統管理員權限，才能完成下列工作：

|區域圖|工作|如需詳細資訊|
|----------|----------|--------------------------|
|安裝|安裝 Visual Studio。|[安裝 Visual Studio](../install/install-visual-studio.md)|
||安裝、更新或移除本機說明內容。|[安裝與管理本機內容](../ide/install-and-manage-local-content.md)|
|應用程式類型|開發適用於 SharePoint 的方案。|[開發 SharePoint 方案的需求](/office-dev/office-dev/requirements-for-developing-sharepoint-solutions)|
||取得 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]的開發人員授權。|[取得開發人員授權](http://go.microsoft.com/fwlink/?LinkID=241313)|
|工具箱|將傳統 COM 控制項新增至 [工具箱]。|[工具箱](../ide/reference/toolbox.md)|
|增益集|安裝及使用在 IDE 中使用傳統 COM 撰寫的增益集。|[建立增益集和精靈](http://msdn.microsoft.com/Library/c5a47c21-6668-4de3-898d-afa969317e73)|
|建置|使用註冊元件的建置後事件。|[了解自訂建置步驟和建置事件](/cpp/ide/understanding-custom-build-steps-and-build-events)|
||包含當您建立 C++ 專案時的註冊步驟。|[了解自訂建置步驟和建置事件](/cpp/ide/understanding-custom-build-steps-and-build-events)|
|偵錯|偵錯以更高權限執行的應用程式。|[偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)|
||偵錯在不同使用者帳戶下執行的應用程式，例如 ASP.NET 網站。|[偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)|
||在 XAML 瀏覽器應用程式的區域 (XBAP) 中進行偵錯。|[WPF 主應用程式 (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||使用模擬器來偵錯 Microsoft Azure 雲端服務專案。|[在 Visual Studio 中偵錯雲端服務](http://go.microsoft.com/fwlink/?LinkId=266725)|
||設定遠端偵錯的防火牆。|[遠端偵錯](../debugger/remote-debugging.md)|
|效能工具|對應用程式進行程式碼剖析。|[效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)|
|部署|將 Web 應用程式部署在本機電腦上的 Internet Information Services (IIS)。|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment](http://go.microsoft.com/fwlink/?LinkId=266478) (使用 Visual Studio 或 Visual Web Developer 將 ASP.NET Web 應用程式部署至主機服務提供者：部署至 IIS 作為測試環境)|

## <a name="running-visual-studio-as-an-administrator"></a>以系統管理員身分執行 Visual Studio

您可以在每次啟動 IDE 時以系統管理權限啟動 Visual Studio，或修改應用程式捷徑永遠以系統管理權限執行。 如需詳細資訊，請參閱 Windows 說明。

### <a name="to-run-visual-studio-with-administrative-permissions"></a>以系統管理權限執行 Visual Studio

這些指示適用於 Windows 10。 其他 Windows 版本的指示與這些相似。

1. 開啟 [開始] 功能表，然後捲動至 Visual Studio 2017。

1. 從 **Visual Studio 2017** 的操作功能表 (按一下滑鼠右鍵)，選取 [更多] > [以系統管理員身分執行]。

     在 Visual Studio 啟動時，**(系統管理員)** 會顯示在標題列的產品名稱之後。

## <a name="see-also"></a>另請參閱

- [移植、移轉和升級 Visual Studio 專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [安裝 Visual Studio](../install/install-visual-studio.md)