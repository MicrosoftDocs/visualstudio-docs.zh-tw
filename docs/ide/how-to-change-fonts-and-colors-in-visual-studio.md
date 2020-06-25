---
title: 變更字型與色彩
ms.date: 06/01/2020
ms.topic: how-to
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0eb2373117b382cb19f374581ada45a5732b9c4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284672"
---
# <a name="how-to-change-fonts-and-colors-in-visual-studio"></a>如何：變更 Visual Studio 中的字型和色彩

您可以透過許多方式來變更 Visual Studio 中的字型和色彩。 例如，您可以將預設藍色主題變更為深色主題（也稱為「深色模式」）。而且，您可以將預設字型和文字大小變更為不同的字型和大小。

## <a name="change-the-color-theme"></a>變更色彩佈景主題

以下是如何在 Visual Studio 中變更 IDE 框架和工具視窗的色彩主題。

1. 在功能表列上，選擇 [**工具**] [  >  **選項**]。

1. 在 [選項] 清單中，選擇 [**環境**]  >  **[一般**]。

1. 在 [**色彩主題**] 清單中，選擇 [預設的**藍色**主題]、[**淺色**主題]、[**深色**主題] 或 [**藍色（更高對比）** ] 主題。

   ![[選項] 對話方塊的螢幕擷取畫面，用來變更色彩主題](media/fonts-colors-theme.png "[選項] 對話方塊的螢幕擷取畫面，您可以用來變更色彩主題")

    > [!NOTE]
    > 當您變更色彩主題時，IDE 中的文字會還原為該主題的預設或先前自訂的字型和大小。

    :::moniker range="vs-2017"

    > [!TIP]
    > 您可以藉由安裝[Visual Studio 2017 的色彩主題編輯器](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)，來建立和編輯自己的 Visual Studio 主題。

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > 您可以藉由安裝[Visual Studio 色彩主題設計](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)工具來建立和編輯自己的 Visual Studio 主題。

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>變更字型和文字大小

您可以變更所有 IDE 框架和工具視窗的字型和文字大小，或僅針對特定的視窗或文字元素。 您也可以變更編輯器中的字型和文字大小。

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>變更 IDE 中的字型和文字大小

1. 在功能表列上，選擇 [**工具**] [  >  **選項**]。

1. 在 [選項] 清單中，選擇 [**環境**] [字型  >  **和色彩**]。

1. 在 [**顯示設定**] 清單中，選擇 [**環境**]。

   ![[選項] 對話方塊的螢幕擷取畫面，用來變更 IDE 中的字型和色彩](media/fonts-colors-environment.png "[選項] 對話方塊的螢幕擷取畫面，用來變更 IDE 中的字型和色彩")

    > [!NOTE]
    > 如果您想要只變更工具視窗的字型，請在 [顯示設定]**** 清單中選擇 [所有文字工具視窗]****。

1. 修改 [**字型**] 和 [**大小**] 選項，以變更 IDE 的字型和文字大小。

1. 選取 [顯示項目]**** 中的適當項目，然後修改 [項目前景]**** 和 [項目背景]**** 選項。

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>變更編輯器中的字型和文字大小

1. 在功能表列上，選擇 [**工具**] [  >  **選項**]。

1. 在 [選項] 清單中，選擇 [**環境**] [字型  >  **和色彩**]。

1. 在 [**顯示設定**] 清單中，選取 [**文字編輯器**]。

   ![[選項] 對話方塊的螢幕擷取畫面，用來變更編輯器中的字型和色彩](media/fonts-colors-text-editor.png "[選項] 對話方塊的螢幕擷取畫面，用來變更編輯器中的字型和色彩")

1. 修改 [**字型**] 和 [**大小**] 選項，以變更編輯器的字型和文字大小。

1. 選取 [顯示項目]**** 中的適當項目，然後修改 [項目前景]**** 和 [項目背景]**** 選項。

如需詳細資訊，請參閱[變更編輯器的字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)頁面。

## <a name="accessibility-options"></a>協助工具選項

如果您遇到較低的願景，會有色彩主題選項可供您選擇。 您可以針對電腦上的*所有*應用程式和 UI 使用高對比選項，或僅針對 Visual Studio 的額外 [對比度] 選項。

### <a name="use-windows-high-contrast"></a>使用 Windows 高對比

使用下列其中一個程式來切換 Windows 高對比選項：

- 在 Windows 或任何 Microsoft 應用程式中，按**左 Alt** + **左 Shift** + **PrtScn**鍵。

- 在 Windows 中，選擇 [**開始**  >  **設定**] [  >  **輕鬆存取**  >  **高對比**]。

    > [!WARNING]
    > Windows 高對比設定會影響電腦上的所有應用程式和 UI。

### <a name="use-visual-studio-extra-contrast"></a>使用 Visual Studio 額外的對比

使用下列程式來切換 Visual Studio 額外的對比選項：

1. 在 [Visual Studio] 的功能表列上，選擇 [**工具**] [  >  **選項**]，然後在 [選項] 清單中選擇 [**環境**]  >  **[一般**]。

1. 在 [**色彩主題**] 下拉式清單中，選擇 [**藍色（更高對比）** ] 主題，然後選擇 [**確定]**。

若要深入瞭解其他可供您使用的 Visual Studio 協助工具選項，請參閱 Visual Studio 頁面的[協助工具功能](../ide/reference/accessibility-features-of-visual-studio.md)。

> [!TIP]
> 如果您認為可能有用但目前無法在 Visual Studio 中使用的色彩或字型有協助工具選項，請在[Visual Studio 開發人員社區](https://developercommunity.visualstudio.com/)中選取 [**建議功能**]，讓我們知道。 如需有關此論壇及其運作方式的詳細資訊，請參閱[建議功能](../ide/suggest-a-feature.md)頁面。

## <a name="next-steps"></a>後續步驟

若要深入瞭解您可以變更字型和色彩配置的所有使用者介面（UI）元素的詳細資訊，請參閱[字體和色彩、環境、選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)頁面。

## <a name="see-also"></a>另請參閱

- [變更程式碼編輯器的字型和色彩](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Visual Studio 程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)