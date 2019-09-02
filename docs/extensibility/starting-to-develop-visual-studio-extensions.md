---
title: 開始開發 Visual Studio 延伸模組 |Microsoft Docs
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
ms.openlocfilehash: 3a22e867fe043437e76ebbf61220dd2adda89c12
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822320"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>開始開發 Visual Studio 擴充功能

如果您之前從未寫過 Visual Studio 的延伸模組, 您可能會遇到一些問題。 這裡列出了一些最常見的部分。 如果您沒有看到您要尋找的資訊, 請使用 [意見反應] 按鈕 (畫面底部的 [**此頁面有説明嗎？** ]) 來詢問您想要的內容。

> [!NOTE]
> 本文適用于 Windows 上的 Visual Studio。 如 Visual Studio for Mac, 請參閱[擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)。

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>開發 Visual Studio 擴充功能需要哪些軟體？

除了 Visual Studio 之外, 您還需要安裝 Visual Studio SDK, 才能開發 Visual Studio 延伸模組。 您可以安裝 Visual Studio SDK 做為一般安裝的一部分, 也可以稍後再安裝。 如需有關安裝 Visual Studio SDK 的詳細資訊, 請參閱[VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>我可以使用 Visual Studio 延伸模組來做哪些事？

想像不同 Visual Studio 延伸模組時, 天空的限制。 當然, 大部分的擴充功能都有與撰寫程式碼有關的作業, 但這種情況不一定如此。 以下是您可以建立之延伸類型的一些範例:

- 支援不包含在 Visual Studio 中的語言, 語法著色、IntelliSense 和編譯器和偵錯工具支援

- 使用額外的範本、程式碼重構、新的對話方塊或工具視窗擴充核心 IDE 體驗的生產力工具

- 適用于資料設計或雲端支援等案例的特定領域設計工具

如需擴充功能的範例, 請參閱[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 許多延伸模組都是開放原始碼, 而 Marketplace 則包含其 GitHub 存放庫的連結。

## <a name="which-visual-studio-features-can-i-extend"></a>我可以擴充哪些 Visual Studio 功能？

理論上, 您可以擴充 Visual Studio 的任何部分: 功能表、工具列、命令、視窗、方案、專案、編輯器等等。

在實務上, 我們發現大部分的人都想要擴充的功能是命令、功能表和工具列、windows、IntelliSense 和專案。 以下是相關章節的連結:

- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md): 將您自己的專案新增至 Visual Studio 功能表和工具列。 您可以使用它們來啟動新的 Visual Studio 功能或您自己的外部 helper 應用程式。 您也可以提供功能表項目的自訂快捷方式。

- [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md): 擴充現有的工具視窗, 或建立您自己的工具視窗。 例如, 您可以將新的屬性加入至**屬性**, 或建立新的工具視窗來加入其他功能。

- [編輯器和語言服務延伸](../extensibility/editor-and-language-service-extensions.md)模組: 新增您自己的自訂 Visual Studio 語言提供的 IntelliSense, 或建立新程式設計語言的支援。 您可以建立新的語句完成、建議和新的 QuickInfo 工具提示。 透過 light 燈泡, 您可以加入重構建議和程式碼修正, 以支援新的程式設計語言。

- [擴充專案](../extensibility/extending-projects.md)

- [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)

- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="BKMK_ProjectTemplate"></a>VSSDK 會提供哪些專案範本？
 兩種主要的延伸模組類型為 Vspackage 和 MEF 延伸模組。 一般而言, VSPackage 延伸模組會用於使用或擴充命令、工具視窗和專案的延伸模組。 MEF 延伸模組是用來擴充或自訂 Visual Studio 編輯器。

 針對視覺C#效果和 Visual Basic 擴充功能, VSSDK 會提供空白的 VSIX 專案範本, 您可以將它與建立功能表命令、工具視窗和編輯器擴充功能的新專案範本搭配使用。 您也可以使用此範本來封裝專案範本、程式碼片段和其他成品, 以散發給其他使用者。

 若C++為, VSPackage wizard 會提供程式碼來新增功能表命令、工具視窗和自訂編輯器。

 獨立模式 Shell 範本是用來封裝某個版本的 Visual Studio Shell 中的延伸模組, 您可以用自己的品牌和散發。 下列主題說明如何開始使用各種類型的擴充功能:

- 功能表命令:[建立具有功能表命令的擴充功能](../extensibility/creating-an-extension-with-a-menu-command.md)

- 工具視窗:[使用工具視窗建立擴充功能](../extensibility/creating-an-extension-with-a-tool-window.md)

- 編輯器延伸模組:[使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- 基本 Vspackage:[使用 VSPackage 建立擴充功能](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX 專案範本:[開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>如何? 讓我的延伸模組看起來像 Visual Studio 嗎？
 在[Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中, 為您的擴充功能設計 UI, 取得絕佳的秘訣。

## <a name="where-can-i-find-examples-of-vssdk-code"></a>哪裡可以找到 VSSDK 程式碼的範例？
 上一節中所列的每個連結都有逐步解說, 示範如何執行特定功能。 您也可以在 GitHub 上找到[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中的開放原始碼 VSSDK 範例。

## <a name="how-can-i-distribute-my-extension"></a>如何散發我的擴充功能？
 您可以在另一部電腦上安裝您的擴充功能, 或將其以 .vsix 檔案的形式傳送給朋友, 您可以按兩下該檔案來安裝。 您可以在出[貨 Visual Studio 延伸](../extensibility/shipping-visual-studio-extensions.md)模組中找到更多有關 VSIX 封裝的資訊。

 您也可以在 Visual Studio Marketplace 上發佈延伸模組, 如此一來, 大量的 Visual Studio 客戶就能看到它。 如需將擴充功能封裝到 Marketplace 的範例, 請[參閱逐步解說:發行 Visual Studio 延伸](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)模組。 如需有關要在 Marketplace 上發佈之事項的詳細資訊, 請參閱[Visual Studio 的產品和延伸](/azure/devops/extend/overview?view=vsts)模組。

## <a name="see-also"></a>另請參閱

- [擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)