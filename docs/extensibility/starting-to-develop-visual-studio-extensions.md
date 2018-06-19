---
title: 開始開發 Visual Studio 擴充功能 |Microsoft 文件
ms.custom: ''
ms.date: 09/18/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44403b5d60fc13666ffc6ec00558b80ef3a50ea9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144459"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>開始開發 Visual Studio 擴充功能
如果您永遠不會編寫 Visual Studio 擴充功能之前，您可能會有一些問題。 我們已列出一些最常見的。 如果您沒有看到您要尋找的資訊，請使用意見反應按鈕 (**本頁很有幫助？** 螢幕的底部) 以取得您想要。  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>若要開發 Visual Studio 擴充功能是否需要哪些軟體？  
 您需要安裝 Visual Studio SDK 除了 Visual Studio，若要開發 Visual Studio 擴充功能。 您可以安裝 Visual Studio SDK 一部分一般安裝，或您可以在稍後安裝。 如需有關如何安裝 Visual Studio SDK 的詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>使用 Visual Studio 擴充功能可以做的事情種類？  
 想像不同 Visual Studio 擴充功能時，sky 的限制。 當然，大部分的擴充功能必須與撰寫程式碼，但不可以是這種情況。 以下是您可以建立延伸模組種類的一些範例：  
  
-   未隨附在 Visual Studio 中的語法著色、 IntelliSense 和編譯器和偵錯支援的語言的支援  
  
-   擴充核心的產能工具與其他的範本、 程式碼重構，新對話或工具視窗的 IDE 體驗  
  
-   定義域專屬設計或雲端支援的資料等案例的設計工具  
  
 如需擴充功能的範例，請參閱[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 許多擴充功能已開啟來源，且 Marketplace 包括其 GitHub 儲存機制的連結。 
  
## <a name="which-visual-studio-features-can-i-extend"></a>可以擴充 Visual Studio 功能？  
 在理論上，您可以擴充 Visual Studio 的任何一部分： 功能表、 工具列、 命令、 windows、 方案、 專案、 編輯器和等等。  
  
 實際上，我們發現大多數人想要擴充的功能是命令、 功能表和工具列、 windows、 IntelliSense 和專案。 相關章節的連結如下：  
  
-   [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)： 將您自己的項目加入至 Visual Studio 功能表和工具列。 您可以使用它們來啟動 Visual Studio 功能或您自己的外部協助應用程式。 您也可以提供自訂的捷徑功能表項目的。  
  
-   [延伸和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)： 擴充現有的工具視窗或建立您自己的工具視窗。 比方說，您可以在其中加入新的屬性以**屬性**，或者您可以建立新的工具視窗，加入其他功能。  
  
-   [編輯器和語言服務延伸](../extensibility/editor-and-language-service-extensions.md)： 新增您自己的自訂 IntelliSense 提供的 Visual Studio 語言，或建立新的程式設計語言的支援。 您可以建立新的陳述式完成、 建議和新 QuickInfo 工具提示。 燈泡，您可以新增重構的建議與修正以支援新的程式設計語言的程式碼。  
  
-   [擴充專案](../extensibility/extending-projects.md)  
  
-   [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)  
  
-   [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> VSSDK 提供何種專案範本？  
 兩個主要類型的擴充功能是 Vspackage 和 MEF 擴充功能。 一般情況下，VSPackage 擴充功能可用的擴充功能的使用或擴充命令、 工具視窗和專案。 MEF 擴充功能可用來擴充或自訂 Visual Studio 編輯器。  
  
 針對 Visual C# 和 Visual Basic 的擴充功能，VSSDK 提供空的 VSIX 專案範本，就可以將新的項目範本建立功能表命令、 工具視窗，以及編輯器延伸模組搭配使用。 您也可以使用此範本封裝專案範本、 程式碼片段和其他成品以散發給其他使用者。  
  
 C + +，VSPackage 精靈會提供程式碼以加入功能表命令、 工具視窗和自訂編輯器。  
  
 Isolated Shell 範本用來封裝的版本，您可以設定的品牌並發佈為您自己的 Visual Studio shell 擴充功能。 下列主題將示範如何開始使用每一種副檔名：  
  
-   功能表命令：[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   工具視窗：[建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   編輯器延伸模組：[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   基本 Vspackage:[建立 VSPackage 擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX 專案範本：[入門 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolated shell:[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>如何取得 my 看起來像是 Visual Studio 的擴充功能？  
 設計您的擴充功能中的 UI 時，取得絕佳的祕訣[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>哪裡可以找到 VSSDK 程式碼的範例？  
 每個連結上一節中所列有逐步解說，示範如何實作特定功能。 您也可以尋找開放原始碼 GitHub 上的 VSSDK 範例[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。  
  
## <a name="how-can-i-distribute-my-extension"></a>我要如何散發 my 擴充功能？  
 您可以在另一部電腦上安裝您的擴充功能，或將它傳送給您的朋友為.vsix 檔案，按兩下安裝。 您可以進一步了解在 VSIX 封裝[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
 您也可以發佈您的擴充功能，可讓您更大量的 Visual Studio 客戶看到 Visual Studio Marketplace 上。 如需封裝至 Marketplace 擴充功能的範例，請參閱[逐步解說： 發行 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 如需您需要如何在 Marketplace 上發佈的詳細資訊，請參閱[產品和用於 Visual Studio 擴充功能](/vsts/integrate/ide/extensions/overview)。
