---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c338648ebb69874781906c0eabff670e5158be8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050903"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK 可協助您擴充 Visual Studio 功能或整合到 Visual Studio 的新功能。 您可以散發給其他使用者，以及 Visual Studio 組件庫延伸模組。 下列是一些可擴充 Visual Studio 的方法：  
  
- 將命令、 按鈕、 功能表和其他 UI 項目加入 IDE  
  
- 加入新功能的工具視窗  
  
- 將 IntelliSense 擴充指定的語言，或提供 IntelliSense 對新的程式設計語言  
  
- 使用燈泡來提供提示與建議，協助開發人員撰寫更好的程式碼  
  
- 啟用新語言的支援  
  
- 加入自訂的專案類型  
  
- 接觸上百萬名開發人員從 Visual Studio marketplace  
  
  如果您從未撰寫過 Visual Studio 擴充功能之前，您應該會發現這些功能以及在詳細資訊[開始開發 Visual Studio 擴充功能](../extensibility/starting-to-develop-visual-studio-extensions.md)。  
  
## <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>什麼是 Visual Studio 2015 SDK 的新功能  
 Visual Studio SDK 有一些新的功能，包括燈泡和新的專案項目可讓您建立功能表命令、 工具視窗和編輯器延伸模組使用 VSIX 封裝。 如需詳細資訊，請參閱 < [What's New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 使用者體驗方針  
 設計您的延伸模組的使用者介面時，取得絕佳的祕訣[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
 您也可以了解如何讓您看起來很讚高 DPI 裝置上的延伸模組我們[定址 DPI 問題](../extensibility/addressing-dpi-issues2.md)主題。  
  
 善用[映像服務與資料庫目錄](../extensibility/image-service-and-catalog.md)絕佳的映像管理和支援高 DPI 和佈景主題。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>尋找和安裝現有的 Visual Studio 擴充功能  
 您可以找到 Visual Studio 擴充功能**擴充功能和更新** 對話方塊上的**工具**功能表。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。 您也可以找到擴充功能中的[Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 參考  
 您可以尋找在 Visual Studio SDK API 參考[Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 範例  
 您可以在 GitHub 上找到的 VS SDK 延伸模組的開放原始碼範例[Visual Studio 範例](https://aka.ms/vs2015sdksamples)。 此 GitHub 存放庫包含範例，示範 Visual Studio 中的各種擴充功能。  
  
## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 資源  
 如果您有關於 VSSDK 的問題，或想要共用您的體驗，開發擴充功能，您可以使用[Visual Studio 擴充性論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS 群組聊天](https://gitter.im/Microsoft/extendvs)。  
  
 您可以找到詳細資訊[VSX Arcana 部落格](http://blogs.msdn.com/b/vsx/)和 Microsoft Mvp 所撰寫的部落格的數目：  
  
- [最愛的 Visual Studio 擴充功能](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
- [Visual Studio 擴充性](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [擴充 Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>另請參閱  
 [Creating an Extension with 功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [如何：將擴充性專案移轉至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [常見問題集：將增益集轉換成 VSPackage 擴充功能](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [管理多個執行緒以 Managed 程式碼](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [將命令加入至工具列](../extensibility/adding-commands-to-toolbars.md)   
 [擴充和自訂工具 Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [編輯器和語言服務延伸模組](../extensibility/editor-and-language-service-extensions.md)   
 [擴充專案](../extensibility/extending-projects.md)   
 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)   
 [建立自訂專案與項目範本](../extensibility/creating-custom-project-and-item-templates.md)   
 [擴充屬性和 [屬性] 視窗](../extensibility/extending-properties-and-the-property-window.md)   
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用和提供服務](../extensibility/using-and-providing-services.md)   
 [擴充已連線的服務](../extensibility/extending-connected-services.md)   
 [管理 Vspackage](../extensibility/managing-vspackages.md)   
 [Visual Studio 獨立模式 Shell](../extensibility/visual-studio-isolated-shell.md)   
 [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)   
 [深入探索 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK 支援](../extensibility/support-for-the-visual-studio-sdk.md)   
 [封存](../extensibility/archive.md)   
 [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)
