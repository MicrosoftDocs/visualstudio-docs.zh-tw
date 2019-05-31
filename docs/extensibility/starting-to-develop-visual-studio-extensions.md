---
title: 開始開發 Visual Studio 擴充功能 |Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4a3978ba229dff5f5888a50bf67d263cc2c614e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331762"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>開始開發 Visual Studio 擴充功能

如果您從未撰寫過 Visual Studio 擴充功能之前，您可能會有一些問題。 我們已列出一些最常見的。 如果您沒有看到您要尋找的資訊，請使用意見反應按鈕 (**此頁面是否有幫助？** 螢幕的底部)，要求提供您想要。

> [!NOTE]
> 這篇文章適用於在 Windows 上的 Visual Studio。 Visual Studio for Mac，請參閱 <<c0> [ 擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)。

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>我需要哪些軟體開發的 Visual Studio 延伸模組？

必須先安裝 Visual Studio SDK 除了 Visual Studio，以便開發 Visual Studio 擴充功能。 您可以安裝 Visual Studio SDK，一般的安裝程序，或您可以在稍後安裝。 如需有關如何安裝 Visual Studio SDK 的詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>使用 Visual Studio 擴充功能可以做的事情種類？

為整個天際限制難想像不同的 Visual Studio 擴充功能。 當然，大部分的擴充功能和撰寫程式碼，但，沒有這種情況。 以下是一些範例，您可以建置的延伸模組的類型：

- 不隨附在 Visual Studio 中，語法著色、 IntelliSense 和編譯器和偵錯支援的語言的支援

- 擴充核心的產能工具 IDE 體驗的其他範本、 程式碼重構、 新的對話方塊或 工具視窗

- 定義域專屬設計工具，像是資料設計] 或 [雲端支援的案例

如需擴充功能的範例，請參閱[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 許多擴充功能已開啟，並 Marketplace 包含連結至其的 GitHub 存放庫。

## <a name="which-visual-studio-features-can-i-extend"></a>可以擴充 Visual Studio 功能？

理論上，您可以擴充 Visual Studio 的任何一部分： 功能表、 工具列、 指令、 windows、 方案、 專案、 編輯器和等等。

在實務上，我們發現大多數人想要擴充的功能是命令、 功能表和工具列、 windows、 IntelliSense 和專案。 以下是相關章節的連結：

- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)： 將您自己的項目新增至 Visual Studio 功能表和工具列。 您可以使用它們來啟動 Visual Studio 的新功能或您自己的外部協助應用程式。 您也可以提供自訂快速鍵的功能表項目。

- [延伸和自訂工具 Windows](../extensibility/extending-and-customizing-tool-windows.md)： 擴充現有的工具視窗，或建立您自己的工具視窗。 比方說，您可以在其中新增新的屬性以**屬性**，也可以建立新的工具視窗，以加入其他功能。

- [編輯器和語言服務延伸模組](../extensibility/editor-and-language-service-extensions.md)： 新增您自己的自訂 Visual Studio 語言提供的 IntelliSense，或建立新的程式設計語言的支援。 您可以建立新的陳述式完成、 建議和新 QuickInfo 工具提示。 燈泡，您可以新增重構的建議和程式碼修正來支援新的程式設計語言。

- [擴充專案](../extensibility/extending-projects.md)

- [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)

- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](/visualstudio/extensibility/shell/visual-studio-isolated-shell)

## <a name="BKMK_ProjectTemplate"></a> 哪些專案範本所提供的 VSSDK？
 延伸模組的兩個主要類型都是 Vspackage 和 MEF 擴充功能。 一般情況下，VSPackage 擴充功能可使用或擴充命令、 工具視窗和專案的延伸模組。 MEF 擴充功能用來擴充或自訂 Visual Studio 編輯器中。

 Visual C# 和 Visual Basic 擴充功能，VSSDK 提供空白的 VSIX 專案範本，您可以使用與建立功能表命令、 工具視窗和編輯器延伸模組的新項目範本。 您也可以使用此範本以封裝專案範本、 程式碼片段和其他成品以散發給其他使用者。

 針對C++，VSPackage 精靈提供的程式碼，以加入功能表命令、 工具視窗和自訂編輯器。

 Isolated Shell 範本用來封裝的版本，您可以加上商標及散發為您自己的 Visual Studio shell 擴充功能。 下列主題會示範如何開始使用每種類型的延伸模組：

- 功能表命令：[建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)

- 工具視窗：[使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)

- 編輯器擴充功能：[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- 基本的 Vspackage 中：[使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX 專案範本：[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>如何取得我看起來像是 Visual Studio 的擴充功能？
 設計您的延伸模組的使用者介面時，取得絕佳的祕訣[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。

## <a name="where-can-i-find-examples-of-vssdk-code"></a>哪裡可以找到 VSSDK 程式碼的範例？
 上一節中所列的每個有逐步解說，示範如何實作特定的功能。 您也可以尋找開放原始碼在 GitHub 上的 VSSDK 範例[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

## <a name="how-can-i-distribute-my-extension"></a>我要如何散發 my 擴充功能？
 您可以在另一部電腦上安裝擴充功能，或將它傳送給您的朋友為.vsix 檔案，按兩下安裝。 您可以深入了解在 VSIX 封裝[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。

 您也可以發佈您的延伸模組，可讓您更大量的 Visual Studio 客戶看到 Visual Studio Marketplace 上。 封裝至 Marketplace 延伸模組的範例，請參閱[逐步解說：發行 Visual Studio 擴充功能](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 如需有關您要如何在 Marketplace 上發佈的詳細資訊，請參閱 <<c0> [ 產品和 Visual Studio 擴充功能](/azure/devops/extend/overview?view=vsts)。

## <a name="see-also"></a>另請參閱

- [擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)