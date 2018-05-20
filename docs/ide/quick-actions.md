---
title: 快速動作、燈泡及螺絲起子
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d413d5b440c39c3603e1e909fb0c4645719f188b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="quick-actions"></a>快速動作

快速動作可讓您輕鬆地重構、產生或用其他方式以單一動作修改程式碼。 快速動作可供 C#、[C++](/cpp/ide/writing-and-refactoring-code-cpp) 和 Visual Basic 程式碼檔案使用。 有些動作適用於特定程式設計語言，其他則適用於所有語言。

快速動作可用於：

- 針對[程式碼分析器](../code-quality/roslyn-analyzers-overview.md)規則的違規情況套用程式碼修正
- [隱藏](../code-quality/use-roslyn-analyzers.md)程式碼分析器規則的違規情況
- 套用重構作業 (例如，[內嵌暫存變數](../ide/reference/inline-temporary-variable.md))
- 產生程式碼 (例如，[引進區域變數](../ide/reference/introduce-local-variable.md))

快速動作的套用方式包括使用燈泡 ![燈泡圖示](media/light-bulb-icon.png) 或螺絲起子 ![螺絲起子圖示](media/screwdriver-icon.png) 圖示，以及按 **Ctrl**+**.** 當游標位於可使用動作的程式碼行上時。 如果有紅色波浪線指出錯誤，而且 Visual Studio 有該錯誤可用的修正程式，您就會看到錯誤燈泡 ![錯誤燈泡圖示](media/error-light-bulb-icon.png)。

好比說，協力廠商可以針對任何語言，在 SDK 當中提供自訂診斷和建議，而 Visual Studio 燈泡會依據這些規則亮燈。

## <a name="icons"></a>圖示

當有快速動作可用時，顯示的圖示會指出可用的修正或重構類型。 「螺絲起子」![螺絲起子圖示](media/screwdriver-icon.png)圖示表示有可變更程式碼的動作，但不一定要使用。 「黃色燈泡」![燈泡圖示](media/light-bulb-icon.png)圖示表示有「應」執行的動作，以改善程式碼。 「錯誤燈泡」![錯誤燈泡圖示](media/error-light-bulb-icon.png)圖示表示有動作可修正您程式碼中的錯誤。

## <a name="to-see-a-light-bulb-or-screwdriver"></a>顯示燈泡或螺絲起子

- 如果有可用的修正，燈泡會在您將滑鼠暫留於錯誤位置的同時顯示。

   ![當滑鼠游標暫留時的燈泡](../ide/media/vs2015_lightbulb_hover.png)

- 燈泡和螺絲起子會在您將游標移到可使用快速動作的程式碼上時，顯示在編輯器的左側邊界。

- 在字行任何地方按 **Ctrl**+**.**， 即可看到可用快速動作與重構的清單。

## <a name="to-see-potential-fixes"></a>如何看到可能的修正方法

選取燈泡旁的向下箭號或 [顯示可能的修正] 連結，就會顯示可用的快速動作清單。

![放大的燈泡](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼產生](../ide/code-generation-in-visual-studio.md)
- [常用的快速動作](../ide/common-quick-actions.md)
- [程式碼樣式及快速動作](../ide/code-styles-and-quick-actions.md)
- [撰寫和重構程式碼 (C++)](/cpp/ide/writing-and-refactoring-code-cpp)