---
title: 開始開發視覺化工作室擴展 |微軟文件
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
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699732"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>開始開發 Visual Studio 擴充功能

如果您以前從未編寫過 Visual Studio 擴展,您可能有一些問題。 我們在此處列出了一些最常見的。 如果您沒有看到要尋找的資訊,請使用回饋按鈕(**此頁面有説明嗎?** 螢幕底部)詢問您想要什麼。

> [!NOTE]
> 本文適用於 Windows 上的可視化工作室。 有關 Mac 的視覺工作室,請參閱[為 Mac 擴展視覺工作室](/visualstudio/mac/extending-visual-studio-mac)。 有關視覺化工作室代碼,請參閱[可視化工作室代碼擴展 API](https://code.visualstudio.com/api)。

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>開發 Visual Studio 擴展需要什麼軟體?

除了可視化工作室之外,您還需要安裝 Visual Studio SDK,以便開發可視化工作室擴展。 您可以將 Visual Studio SDK 作為常規設置的一部分安裝,也可以稍後安裝它。 有關安裝視覺化工作室 SDK 的詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>我可以使用 Visual Studio 擴充做什麼?

天空是想像不同的視覺工作室擴展的極限。 當然,大多數擴展與編寫代碼有關,但事實並非如此。 以下是您可以建構的擴充型態的範例:

- 支援 Visual Studio 中未包含的語言,包括語法著色、IntelliSense 以及編譯器和除錯支援

- 以其他樣本、程式碼重構、新對話框或工具視窗延伸核心 IDE 體驗的生產力工具

- 針對資料設計或雲端支援等機制的特定網域設計器

有關擴展的範例,請查看[視覺化工作室市場](https://marketplace.visualstudio.com/vs)。 許多擴展都是開源的,應用商店包括指向其 GitHub 存儲庫的連結。

## <a name="which-visual-studio-features-can-i-extend"></a>我可以擴展哪些視覺工作室功能?

從理論上講,您可以擴展 Visual Studio 的任何部分:功能表、工具列、命令、視窗、解決方案、專案、編輯器等。

在實踐中,我們發現大多數人想要擴展的功能是命令、功能表和工具列、視窗、IntelliSense 和專案。 以下是相關部分的連結:

- [擴展選單和指令](../extensibility/extending-menus-and-commands.md):將您自己的專案添加到 Visual Studio 選單和工具列。 您可以使用它們啟動新的 Visual Studio 功能或您自己的外部説明程式應用程式。 您還可以為功能表項提供自訂快捷方式。

- [擴展和自定義工具視窗](../extensibility/extending-and-customizing-tool-windows.md):擴展現有工具視窗或創建自己的工具視窗。 例如,您可以將新屬性添加到**屬性**,也可以創建新的工具視窗以添加其他功能。

- [編輯器和語言服務擴展](../extensibility/editor-and-language-service-extensions.md):將您自己的自定義項添加到為 Visual Studio 語言提供的 IntelliSense 中,或創建新程式設計語言。 您可以建立新的語句完成、建議和新的 QuickInfo 工具提示。 使用燈泡,您可以添加重構建議和代碼修復以支援新的程式設計語言。

- [擴充專案](../extensibility/extending-projects.md)

- [擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)

- [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)

- [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>VSSDK 提供了哪些項目範本?
 兩種主要類型的擴展是 VSPackages 和 MEF 擴展。 通常,VSPackage 擴展用於使用或擴展命令、工具視窗和專案的擴展。 MEF 擴展用於擴展或自定義可視化工作室編輯器。

 對於 Visual C++ 和 Visual Basic 擴展,VSSDK 提供了一個空的 VSIX 專案範本,您可以將該範本與創建選單命令、工具視窗和編輯器擴展的新專案範本一起使用。 您還可以使用此範本打包專案範本、代碼段和其他專案,以便分發給其他使用者。

 對於C++,VSPackage 精靈提供添加功能表命令、工具視窗和自定義編輯器的代碼。

 隔離的 Shell 範本用於在 Visual Studio 外殼版本中打包擴展,您可以將其品牌化並分發為您自己的版本。 以下主題展示如何開始使用各種延伸:

- 選單指令:[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)

- 工具視窗:[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)

- 編輯器延伸:[使用編輯器樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- 基本 VS 套件:[使用 VS 套件建立延伸](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX 專案樣本:[開始使用 VSIX 專案樣本](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>如何獲取擴展,以看起來像視覺工作室?
 在[可視化工作室用戶體驗指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)中獲取為擴展設計 UI 的提示。

## <a name="where-can-i-find-examples-of-vssdk-code"></a>在哪裡可以找到 VSSDK 代碼的範例?
 上一節中列出的每個連結都有分步演練,演示如何實現特定功能。 您還可以在[Visual Studio 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)的 GitHub 上找到開源 VSSDK 範例。

## <a name="how-can-i-distribute-my-extension"></a>如何分發我的擴展?
 您可以將擴展卡安裝在另一台電腦上,也可以將其作為 .vsix 檔發送給朋友,通過雙擊來安裝該檔。 您可以在[運輸視覺工作室擴展](../extensibility/shipping-visual-studio-extensions.md)處瞭解有關 VSIX 軟體包的更多。

 您還可以在可視化工作室應用商店上發佈擴展,這使得大量視覺工作室客戶可以看到它。 有關將擴展打包到應用商店的範例,請參閱[演練:發佈可視化工作室擴展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 有關在應用商店上發佈需要做什麼的詳細資訊,請參閱[Visual Studio 的產品和擴展](/azure/devops/extend/overview?view=vsts)。

## <a name="see-also"></a>另請參閱

- [擴充 Visual Studio for Mac](/visualstudio/mac/extending-visual-studio-mac)
- [延伸視覺工作室代碼](https://code.visualstudio.com/api)
