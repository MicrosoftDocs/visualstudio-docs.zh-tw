---
title: 使用者權限 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 34eab1bed0113c3fbe39574c9ef2a4c2822af5c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858366"
---
# <a name="user-permissions-and-visual-studio"></a>使用者權限和 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

基於安全性原因，您最好盡可能以一般使用者身分來執行 Visual Studio。

> [!WARNING]
>  您也應該確保不會編譯、啟動或偵錯任何不是來自受信任者或受信任位置的 Visual Studio 方案。

 身為一般使用者，您可以在 Visual Studio IDE 中執行幾乎所有的作業，但是必須有系統管理員權限，才能完成下列工作：

|區域圖|工作|如需詳細資訊|
|----------|----------|--------------------------|
|安裝|安裝 Visual Studio。|[安裝 Visual Studio 2015](../install/install-visual-studio-2015.md)|
||從 Visual Studio 試用版升級。|[如何：從 Visual Studio 試用版升級](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||安裝、更新或移除本機說明內容。|[安裝與管理本機內容](../ide/install-and-manage-local-content.md)|
|應用程式類型|開發 SharePoint 2010 方案。|[開發 SharePoint 方案的需求](http://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||取得 [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]的開發人員授權。|[取得開發人員授權 (Windows 市集應用程式)](http://go.microsoft.com/fwlink/?LinkID=241313)|
|工具箱|將傳統 COM 控制項新增至 [工具箱]。|[使用工具箱](../ide/using-the-toolbox.md)|
|增益集|安裝及使用在 IDE 中使用傳統 COM 撰寫的增益集。|[建立增益集和精靈](http://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|建置|使用註冊元件的建置後事件。|[了解自訂建置步驟和建置事件](http://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||包含當您建立 C++ 專案時的註冊步驟。|[了解自訂建置步驟和建置事件](http://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|偵錯|偵錯以更高權限執行的應用程式。|[偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)|
||偵錯在不同使用者帳戶下執行的應用程式，例如 ASP.NET 網站。|[偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)|
||在 XAML 瀏覽器應用程式的區域 (XBAP) 中進行偵錯。|[WPF 主應用程式 (PresentationHost.exe)](http://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||使用模擬器來偵錯 Microsoft Azure 雲端服務專案。|[在 Visual Studio 中偵錯雲端服務](http://go.microsoft.com/fwlink/?LinkId=266725)|
||設定遠端偵錯的防火牆。|[在裝置上設定遠端工具](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|效能工具|對應用程式進行程式碼剖析。|[效能分析的初級開發人員指南](../profiling/beginners-guide-to-performance-profiling.md)|
|部署|將 Web 應用程式部署在本機電腦上的 Internet Information Services (IIS)。|[ASP.NET Web 應用程式部署至裝載提供者使用 Visual Studio 或 Visual Web Developer:部署至 IIS 做為測試環境](http://go.microsoft.com/fwlink/?LinkId=266478)|
|提供意見給 Microsoft|變更您參與 Visual Studio 客戶經驗改進計畫的方式。|[如何：傳送意見反應](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>以系統管理員身分執行 Visual Studio
 您可以在每次啟動 IDE 時以系統管理權限啟動 Visual Studio，或修改應用程式捷徑永遠以系統管理權限執行。 如需詳細資訊，請參閱 Windows 說明。

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblueserver2includeswinblue-server-2-mdmd"></a>若要在 [!INCLUDE[win8](../includes/win8-md.md)]、[!INCLUDE[win81](../includes/win81-md.md)]、[!INCLUDE[winserver8](../includes/winserver8-md.md)] 或 [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)] 上以系統管理權限執行 Visual Studio

1.  在 [開始] 畫面上鍵入 **Visual Studio**。 您應該會看到您所安裝之 Visual Studio 的版本。

2.  選取您想要啟動的 Visual Studio 版本，然後開啟捷徑功能表 (這會顯示在畫面底部)。 選擇 [以系統管理員身分執行] 。

     在 Visual Studio 啟動時，**(系統管理員)** 會顯示在標題列的產品名稱之後。

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08r2includeswinsvr08-r2-mdmd"></a>若要在 [!INCLUDE[win7](../includes/win7-md.md)] 或 [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)] 上以系統管理權限執行 Visual Studio

1.  選擇 [開始] 功能表上的 [所有程式]。

2.  在 Microsoft Visual Studio <版本> 資料夾中，選取 Visual Studio <版本>，開啟捷徑功能表，然後選擇 以系統管理員身分執行。

     在 Visual Studio 啟動時，**(系統管理員)** 會顯示在標題列的產品名稱之後。

## <a name="see-also"></a>請參閱
 [移植、 移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)[安裝 Visual Studio 2015](../install/install-visual-studio-2015.md)
