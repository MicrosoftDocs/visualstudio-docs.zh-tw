---
title: "Visual Studio SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: "56"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bf8c558d01538d477aee3670b3c119d72a83878d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK，可協助您擴充 Visual Studio 功能，或將新的功能整合到 Visual Studio。 您可以散發給其他使用者，以及 Visual Studio Marketplace 您擴充功能。 下列是一些可擴充 Visual Studio 的方法：  
  
-   將命令、 按鈕、 功能表和其他 UI 項目加入 IDE  
  
-   加入新功能的工具視窗  
  
-   擴充 IntelliSense 對於給定的語言，或提供 IntelliSense 對新的程式設計語言  
  
-   使用提供的提示與建議可協助開發人員撰寫更好的程式碼的燈泡  
  
-   啟用新語言的支援  
  
-   加入自訂專案類型  
  
-   觸達數百萬的開發人員透過 Visual Studio Marketplace  
  
 如果您永遠不會編寫 Visual Studio 擴充功能之前，您應該尋找有關這些功能，而是在的詳細資訊[開始開發 Visual Studio 擴充功能](../extensibility/starting-to-develop-visual-studio-extensions.md)。  
  
## <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK  
 Visual Studio SDK 是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>在 Visual Studio 2017 SDK 最新消息  
 Visual Studio SDK 包含一些新的功能，例如 VSIX v3 格式以及最新變更，這可能需要更新您的擴充功能。 如需詳細資訊，請參閱[What's New in Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 使用者經驗指導方針  
 設計您的擴充功能中的 UI 時，取得絕佳的祕訣[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
 您也可以了解如何讓您看起來不錯，高 DPI 的裝置上的擴充功能我們[定址 DPI 問題](../extensibility/addressing-dpi-issues2.md)主題。  
  
 利用[映像服務與類別目錄](../extensibility/image-service-and-catalog.md)絕佳的映像管理和支援高 DPI 與主題。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>尋找和安裝現有的 Visual Studio 擴充功能  
 您可以找到 Visual Studio 擴充功能中的**擴充功能和更新**對話**工具**功能表。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。 您也可以尋找擴充功能中的[Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 參考  
 您可以尋找在 Visual Studio SDK 的 API 參考[Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 範例  
 您可以在 GitHub 上找到的 VS SDK 延伸模組的開放原始碼範例[Visual Studio 範例](https://aka.ms/vs2015sdksamples)。 此 GitHub 儲存機制包含範例將示範 Visual Studio 中的各種擴充功能。  
  
## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 資源  
 如果您有關於 VSSDK 的問題，或想要共用您的經驗開發擴充功能，您可以使用[Visual Studio 擴充性論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS Gitter 聊天室](https://gitter.im/Microsoft/extendvs)。  
  
 您可以找到更多資訊[VSX Arcana 部落格](http://blogs.msdn.com/b/vsx/)和許多 Microsoft Mvp 所撰寫的部落格：  
  
-   [最愛的 Visual Studio 擴充功能](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Visual Studio 擴充性](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [擴充 Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>請參閱  
 [建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [如何： 將擴充性專案移轉至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [常見問題集： 將增益集轉換為 VSPackage 擴充功能](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [管理多個執行緒在 Managed 程式碼](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [將命令加入至工具列](../extensibility/adding-commands-to-toolbars.md)   
 [擴充及自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)   
 [編輯器和語言服務延伸模組](../extensibility/editor-and-language-service-extensions.md)   
 [擴充專案](../extensibility/extending-projects.md)   
 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)   
 [建立自訂專案與項目範本](../extensibility/creating-custom-project-and-item-templates.md)   
 [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)   
 [擴充 Visual Studio 的其他組件](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [管理 Vspackage](../extensibility/managing-vspackages.md)   
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)   
 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)   
 [在 Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK 支援](../extensibility/support-for-the-visual-studio-sdk.md)   
 [封存](../extensibility/archive.md)   
 [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)
