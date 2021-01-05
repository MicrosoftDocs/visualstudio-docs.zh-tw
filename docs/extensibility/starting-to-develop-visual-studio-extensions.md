---
title: 開始開發 Visual Studio 擴充功能 |Microsoft Docs
description: 瞭解您首次開始撰寫 Visual Studio 擴充功能時，可能會遇到的一些常見問題。
ms.custom: SEO-VS-2020
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da8bd850413d32e5453b7dc312e863832e5f5218
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715258"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>開始開發 Visual Studio 擴充功能

如果您之前從未撰寫過 Visual Studio 的延伸模組，您可能會遇到一些問題。 我們在此列出了一些最常見的專案。 如果您沒有看到您要尋找的資訊，請使用 [意見反應] 按鈕 (**這個頁面是否有説明？** 在畫面的右上方，) 要求您所要的內容。

> [!NOTE]
> 本文適用于 Windows 上的 Visual Studio。 如 Visual Studio for Mac，請參閱 [擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)。 如 Visual Studio Code，請參閱 [Visual Studio Code 擴充功能 API](https://code.visualstudio.com/api)。

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>我需要哪些軟體才能開發 Visual Studio 擴充功能？

除了 Visual Studio 之外，您還需要安裝 Visual Studio SDK，才能開發 Visual Studio 擴充功能。 您可以安裝 Visual Studio SDK 作為一般設定的一部分，也可以稍後再安裝。 如需安裝 Visual Studio SDK 的詳細資訊，請參閱 [安裝 VISUAL STUDIO sdk](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Visual Studio 擴充功能可以做哪些事？

談到想像不同 Visual Studio 延伸模組時的限制。 當然，大部分的擴充功能都與撰寫程式碼有關，但不一定如此。 以下是您可以建立的一些延伸模組類型範例：

- 支援不包含在 Visual Studio 中的語言，語法著色、IntelliSense 和編譯器以及偵錯工具支援

- 使用額外的範本、程式碼重構、新對話方塊或工具視窗擴充核心 IDE 體驗的生產力工具

- 特定領域的設計工具，適用于資料設計或雲端支援等案例

如需擴充功能的範例，請參閱 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 許多延伸模組都是開放原始碼，而 Marketplace 包含 GitHub 存放庫的連結。

## <a name="which-visual-studio-features-can-i-extend"></a>我可以擴充哪些 Visual Studio 功能？

理論上，您可以只延伸 Visual Studio 的任何部分：功能表、工具列、命令、視窗、方案、專案、編輯器等。

在實務上，我們發現大部分的人想要擴充的功能是命令、功能表和工具列、windows、IntelliSense 和專案。 以下是相關章節的連結：

- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)：將您自己的專案加入 Visual Studio 功能表和工具列。 您可以使用它們來啟動新的 Visual Studio 功能或您自己的外部 helper 應用程式。 您也可以提供功能表項目的自訂快捷方式。

- [擴充和自訂工具視窗](../extensibility/extending-and-customizing-tool-windows.md)：擴充現有的工具視窗，或建立您自己的工具視窗。 例如，您可以將新的屬性加入至 **屬性** 中，也可以建立新的工具視窗來加入其他功能。

- [編輯器和語言服務延伸](../extensibility/editor-and-language-service-extensions.md)模組：將您自己的自訂加入至為 Visual Studio 語言提供的 IntelliSense，或建立新程式設計語言的支援。 您可以建立新的語句完成、建議和新的 QuickInfo 工具提示。 使用 light 燈泡，您可以新增重構建議和程式碼修正，以支援新的程式設計語言。

- [擴充專案](../extensibility/extending-projects.md)

- [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)

- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> VSSDK 提供哪些專案範本？
 這兩種主要類型的延伸模組是 Vspackage 和 MEF 延伸模組。 一般而言，VSPackage 擴充功能會用於使用或擴充命令、工具視窗和專案的延伸模組。 MEF 延伸模組是用來擴充或自訂 Visual Studio 編輯器。

 若為 Visual c # 和 Visual Basic 擴充功能，VSSDK 會提供空白的 VSIX 專案範本，您可以將它與建立功能表命令、工具視窗和編輯器擴充功能的新專案範本一起使用。 您也可以使用此範本來封裝專案範本、程式碼片段和其他成品，以散發給其他使用者。

 針對 c + +，VSPackage wizard 會提供程式碼來加入功能表命令、工具視窗和自訂編輯器。

 隔離式 Shell 範本可用來封裝版本的 Visual Studio Shell 中的延伸模組，您可以自行進行品牌和散發。 下列主題示範如何開始使用各種類型的延伸模組：

- 功能表命令：[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能

- 工具視窗：[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能

- 編輯器延伸[模組：使用編輯器專案範本建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)功能

- 基本 Vspackage：[使用 VSPackage 建立延伸](../extensibility/creating-an-extension-with-a-vspackage.md)模組

- VSIX 專案範本： [使用 Vsix 專案範本消費者入門](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>如何? 讓我的延伸模組看起來像 Visual Studio？
 取得在 [Visual Studio 使用者經驗指導方針](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中，為您的擴充功能設計 UI 的絕佳秘訣。

## <a name="where-can-i-find-examples-of-vssdk-code"></a>我可以在哪裡找到 VSSDK 程式碼的範例？
 上一節所列的每個連結都有逐步解說逐步解說，示範如何執行特定功能。 您也可以在 GitHub 上的 [Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)中尋找開放原始碼 VSSDK 範例。

## <a name="how-can-i-distribute-my-extension"></a>如何散發我的延伸模組？
 您可以在另一部電腦上安裝您的延伸模組，或將它傳送至您的朋友作為 .vsix 檔案，您可以按兩下該檔案來安裝它。 您可以在出 [貨 Visual Studio 擴充](../extensibility/shipping-visual-studio-extensions.md)功能，深入瞭解 VSIX 套件。

 您也可以在 Visual Studio Marketplace 上發佈您的延伸模組，讓大量的 Visual Studio 客戶看得到。 如需將擴充功能封裝至 Marketplace 的範例，請參閱 [逐步解說：發行 Visual Studio 延伸](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)模組。 如需在 Marketplace 上發佈的詳細資訊，請參閱 [Visual Studio 的產品和延伸](/azure/devops/extend/overview?view=vsts&preserve-view=true)模組。

## <a name="see-also"></a>請參閱

- [擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)
- [擴充 Visual Studio Code](https://code.visualstudio.com/api)