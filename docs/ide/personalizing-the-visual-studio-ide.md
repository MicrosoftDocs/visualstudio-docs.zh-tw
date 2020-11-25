---
title: 自訂 IDE
description: 瞭解如何以最能支援您自己開發樣式和需求的方式來個人化 Visual Studio IDE。
ms.custom: SEO-VS-2020
ms.date: 11/20/2017
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4acd399aeb9de1d25cbe6abe2b8bba3f347dbc8a
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871453"
---
# <a name="personalize-the-visual-studio-ide"></a>將 Visual Studio IDE 個人化

您可以使用各種不同的方法來個人化 Visual Studio，以最佳方式支援您自己的開發風格與需求。 您的許多設定可在 Visual Studio 執行個體之間漫遊 &mdash; 請參閱[同步設定](../ide/synchronized-settings-in-visual-studio.md)。 本文簡要描述各種不同的個人化設定，以及何處可找到詳細資訊。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[自訂 Visual Studio for Mac IDE](/visualstudio/mac/customizing-the-ide)。

## <a name="default-settings"></a>預設設定

您可以選擇預設的設定集合，以針對您的開發類型最佳化 Visual Studio。 如需詳細資訊，請參閱[環境設定](environment-settings.md)。

## <a name="general-environment-options"></a>一般環境選項

許多個人化選項會透過[環境選項](../ide/reference/general-environment-options-dialog-box.md)對話方塊來公開。 有兩種方法可以存取此對話方塊：

- 在功能表列上選擇 [**工具**  >  **選項**]，如果尚未展開，請展開 [**環境**] 節點。

- 在搜尋方塊中按下 **Ctrl** + **Q**，輸入 **環境**，然後從結果中選擇 [**環境 > 一般**]。

> [!TIP]
> 當 [選項] 對話方塊出現時，您可以在該頁面上按 **F1**，以取得各種不同設定的說明。

## <a name="environment-color-themes"></a>環境色彩佈景主題

若要在 [淺色]、[深色] 和 [藍色] 之間變更色彩主題，請在 [搜尋] 方塊中輸入 **環境** ，然後選擇 [ **環境 > 一般**]。 在 [選項] 對話方塊中，變更 [色彩佈景主題] 選項。

若要變更編輯器中的顏色標示選項，請在 [搜尋] 方塊中輸入 **環境** ，然後選擇 [ **環境 > 字型和色彩**]。 請參閱[如何：變更字型和色彩](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)。

### <a name="main-menu-casing"></a>主功能表大小寫

您可以變更主功能表的下列兩種大小寫設定：[字首大寫] ("File") 與 [全部大寫] ("FILE")。 在 [搜尋] 方塊中輸入 **環境** ，選取 **[環境 > 一般**]，然後將 [ **套用標題案例樣式] 變更為 [功能表列** ] 選項。

### <a name="customize-menus-and-toolbars"></a>自訂功能表與工具列

若要新增或移除功能表或工具列項目，請參閱[如何：自訂功能表和工具列](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)。

::: moniker range="vs-2017"

## <a name="start-page"></a>起始頁

若要為您和小組建立自訂起始頁，請參閱[自訂起始頁](../ide/customizing-the-start-page-for-visual-studio.md)。

::: moniker-end

## <a name="window-layouts"></a>視窗配置

您可以定義和儲存多個視窗配置，並在其間切換。 例如，您可以定義程式碼撰寫時的版面配置，還有用於偵錯的版面配置。 若要排列視窗位置與行為並儲存自訂版面配置，請參閱[自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。

## <a name="external-tools"></a>外部工具

您可以自訂 [工具] 功能表來啟動外部工具。 如需詳細資訊，請參閱[管理外部工具](../ide/managing-external-tools.md)。

## <a name="see-also"></a>另請參閱

- [環境設定](environment-settings.md)
- [Visual Studio IDE 概觀](../get-started/visual-studio-ide.md)
- [快速入門：先查看 Visual Studio IDE](../ide/quickstart-ide-orientation.md)
- [自訂 Visual Studio for Mac IDE](/visualstudio/mac/customizing-the-ide)
