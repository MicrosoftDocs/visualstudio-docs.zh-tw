---
title: 快速動作、燈泡及螺絲起子
description: 瞭解如何使用單一快速動作來重構、產生或以其他方式修改您的程式碼。
ms.custom: SEO-VS-2020
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 967e73748b364e7e41b1773a7fab33831152ab18
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870777"
---
# <a name="quick-actions"></a>快速動作

快速動作可讓您輕鬆地重構、產生或用其他方式以單一動作修改程式碼。 快速動作可供 C#、[C++](/cpp/ide/writing-and-refactoring-code-cpp) 和 Visual Basic 程式碼檔案使用。 有些動作適用於特定程式設計語言，其他則適用於所有語言。

快速動作可用於：

- 針對程式 [代碼分析器](../code-quality/roslyn-analyzers-overview.md) 規則違規套用程式碼修正

::: moniker range=">=vs-2019"

- [隱藏](../code-quality/use-roslyn-analyzers.md#suppress-violations) 程式碼分析器規則違規或 [設定](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) 其嚴重性

::: moniker-end

::: moniker range="vs-2017"

- [隱藏](../code-quality/use-roslyn-analyzers.md#suppress-violations) 程式碼分析器規則違規

::: moniker-end

- 套用重構 (例如， [內嵌暫存變數](../ide/reference/inline-temporary-variable.md)) 

- 產生程式碼 (例如， [引入本機變數](../ide/reference/introduce-local-variable.md)) 

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[重構 (Visual Studio for Mac)](/visualstudio/mac/refactoring)。

您可以使用燈泡燈泡 ![ 圖示 ](media/light-bulb-icon.png) 或螺絲螺絲 ![ 起子圖示圖示或 ](media/screwdriver-icon.png) 按下 **Ctrl** + **.** 來套用快速動作。 當游標位於可使用動作的程式碼行上時。 如果有紅色波浪線指出錯誤，而且 Visual Studio 有適用於該錯誤的修正，您將會看到錯誤燈泡 ![錯誤燈泡圖示](media/error-light-bulb-icon.png)。

例如，協力廠商可以針對任何語言，在 SDK 當中提供自訂診斷和建議，而 Visual Studio 燈泡會依據那些規則來顯示。

## <a name="icons"></a>圖示

當有快速動作可用時，顯示的圖示會指出可用的修正或重構類型。 「螺絲起子」 ![螺絲起子圖示](media/screwdriver-icon.png)圖示表示有可變更程式碼的動作，但不一定要使用。 「黃色燈泡」 ![燈泡圖示](media/light-bulb-icon.png)圖示表示有「應」執行的動作，以改善程式碼。 「錯誤燈泡」 ![錯誤燈泡圖示](media/error-light-bulb-icon.png)圖示表示有動作可修正您程式碼中的錯誤。

## <a name="to-see-a-light-bulb-or-screwdriver"></a>顯示燈泡或螺絲起子

有可用的修正時，燈泡即會出現：

- 當您將滑鼠停留於錯誤位置時

   ![當滑鼠游標暫留時的燈泡](../ide/media/vs2015_lightbulb_hover.png)

- 當您將插入號 (游標) 移至適用的程式碼行時的編輯器左邊界中

您也可以按 **Ctrl** + **。** 即可看到可用快速動作與重構的清單。

若要查看可能的修正，請選取燈泡旁的向下箭號或 [顯示可能的修正] 連結。 隨即顯示可用的 [快速動作] 清單。

![放大的燈泡](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼產生](../ide/code-generation-in-visual-studio.md)
- [一般的快速動作](../ide/common-quick-actions.md)
- [程式碼樣式和快速動作](../ide/code-styles-and-code-cleanup.md)
- [撰寫和重構程式碼 (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [重構 (Visual Studio for Mac)](/visualstudio/mac/refactoring)
