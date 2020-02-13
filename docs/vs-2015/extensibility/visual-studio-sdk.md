---
title: Visual Studio SDK |Microsoft Docs
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
ms.openlocfilehash: 27dce16d9fe02063eae935af96c26184285e583d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850371"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK 可協助您擴充 Visual Studio 功能，或將新功能整合至 Visual Studio。 您可以將擴充功能散發給其他使用者，以及 Visual Studio 資源庫。 下列是一些可擴充 Visual Studio 的方法：  
  
- 將命令、按鈕、功能表和其他 UI 元素新增至 IDE  
  
- 加入工具視窗以取得新功能  
  
- 擴充指定語言的 IntelliSense，或為新的程式設計語言提供 IntelliSense  
  
- 使用 light 燈泡提供提示和建議，協助開發人員撰寫更好的程式碼  
  
- 啟用新語言的支援  
  
- 新增自訂專案類型  
  
- 透過 Visual Studio Marketplace 觸及數百萬名開發人員  
  
  如果您之前從未寫過 Visual Studio 的延伸模組，您應該會發現這些功能的詳細資訊，以及[開始開發 Visual Studio 延伸](../extensibility/starting-to-develop-visual-studio-extensions.md)模組。  
  
## <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK  
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK 的新功能  
 Visual Studio SDK 有一些新功能，包括輕燈泡和新的專案專案，可讓您使用 VSIX 封裝來建立功能表命令、工具視窗和編輯器延伸模組。 如需詳細資訊，請參閱[Visual Studio 2015 SDK 的新功能](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)。  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 使用者體驗方針  
 在[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中，為您的擴充功能設計 UI，取得絕佳的秘訣。  
  
 您也可以透過我們的[定址 DPI 問題](../extensibility/addressing-dpi-issues2.md)主題，瞭解如何讓您的擴充功能在高 DPI 的裝置上看起來很棒。  
  
 利用[映射服務和目錄](../extensibility/image-service-and-catalog.md)來進行絕佳的影像管理，並支援高 DPI 和主題。  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>尋找和安裝現有的 Visual Studio 延伸模組  
 您可以在 [**工具**] 功能表上的 [**擴充功能和更新**] 對話方塊中找到 Visual Studio 的延伸模組。 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。 您也可以在[Visual Studio Marketplace](https://marketplace.visualstudio.com/)中找到擴充功能  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 參考  
 您可以在[VISUAL STUDIO Sdk 參考](../extensibility/visual-studio-sdk-reference.md)中找到 VISUAL STUDIO sdk API 參考。  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 範例  
 您可以在[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中找到 GitHub 上的 VS SDK 擴充功能的開放原始碼範例。 此 GitHub 存放庫包含的範例會說明 Visual Studio 中的各種可擴充功能。  
  
## <a name="other-visual-studio-sdk-resources"></a>其他 Visual Studio SDK 資源  
 如果您對 VSSDK 有任何疑問，或想要分享開發延伸模組的經驗，您可以使用 Visual Studio 擴充性[論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)或[ExtendVS 群組聊天](https://gitter.im/Microsoft/extendvs)。  
  
 您可以在[VSX Arcana blog](https://blogs.msdn.microsoft.com/vsx/)和 Microsoft mvp 所撰寫的許多 blog 中找到詳細資訊：  
  
- [我的最愛 Visual Studio 延伸模組](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Visual Studio 擴充性](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [擴充 Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>請參閱  
 [建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能   
 [如何：將擴充性專案遷移至 Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [常見問題：將增益集轉換成 VSPackage 擴充功能](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [在 Managed 程式碼中管理多個執行緒](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [將命令新增至工具列](../extensibility/adding-commands-to-toolbars.md)   
 [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)   
 [編輯器和語言服務延伸](../extensibility/editor-and-language-service-extensions.md)模組   
 [擴充專案](../extensibility/extending-projects.md)   
 [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)   
 [建立自訂專案和專案範本](../extensibility/creating-custom-project-and-item-templates.md)   
 [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)   
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [使用和提供服務](../extensibility/using-and-providing-services.md)   
 [擴充已連線的服務](../extensibility/extending-connected-services.md)   
 [管理 vspackage](../extensibility/managing-vspackages.md)   
 [Visual Studio 獨立模式 Shell](../extensibility/visual-studio-isolated-shell.md)   
 [運送 Visual Studio 延伸](../extensibility/shipping-visual-studio-extensions.md)模組   
 在[VISUAL STUDIO SDK 中](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [VISUAL STUDIO SDK 的支援](../extensibility/support-for-the-visual-studio-sdk.md)   
 [封存](../extensibility/archive.md)   
 [Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)
