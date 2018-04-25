---
title: 快速動作 | Microsoft Docs
ms.date: 03/28/2018
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
ms.openlocfilehash: 941980eff8fc2474df9555b326278abdb9b26dac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="quick-actions"></a>快速動作

快速動作可讓您輕鬆地重構、產生或用其他方式以單一動作修改程式碼。 快速動作可供 C#、[C++](/cpp/ide/writing-and-refactoring-code-cpp) 和 Visual Basic 程式碼檔案使用。 有些動作適用於特定程式設計語言，其他則適用於所有語言。

快速動作可用於：

- 針對[程式碼分析器](../code-quality/roslyn-analyzers-overview.md)規則的違規情況套用程式碼修正
- [隱藏](../code-quality/use-roslyn-analyzers.md)程式碼分析器規則的違規情況
- 套用重構作業 (例如，[內嵌暫存變數](../ide/reference/inline-temporary-variable.md))
- 產生程式碼 (例如，[引進區域參數](../ide/reference/introduce-local-variable.md))

使用燈泡圖示 ![小燈泡圖示](media/vs2015_lightbulbsmall.png) 或按 **Ctrl**+**.** 來套用快速動作 當游標位於可使用動作的程式碼行上時。 如果有紅色曲線，而且 Visual Studio 有針對如何修正問題的建議，您就會看到燈泡。 例如，如果紅色曲線指出一個錯誤，當該錯誤有可用的修正時，便會出現燈泡。

好比說，協力廠商可以針對任何語言，在 SDK 當中提供自訂診斷和建議，而 Visual Studio 燈泡會依據這些規則亮燈。

## <a name="to-see-a-light-bulb"></a>如何看到燈泡

1. 在許多情況下，燈泡會在您將滑鼠指標停留在錯誤點上方時自動出現；或者，當您將插入號移到含有錯誤的字行時，燈泡會出現在編輯器左邊界。 當您看到紅色曲線時，可以將滑鼠暫留在其上方，即可顯示燈泡。 當您使用滑鼠或鍵盤前往發生問題之字行中的任何地方，也可以使燈泡顯示。

1. 在字行任何地方按 **Ctrl**+**.**， 可叫用燈泡，直接前往可能的修正方法清單。

   ![當滑鼠游標暫留時的燈泡](../ide/media/vs2015_lightbulb_hover.png)

## <a name="to-see-potential-fixes"></a>如何看到可能的修正方法

按一下向下箭號或 [顯示可能的修正方法] 連結，就會顯示燈泡可以提供給您的快速動作清單。

![放大的燈泡](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的程式碼產生](../ide/code-generation-in-visual-studio.md)
- [常用的快速動作](../ide/common-quick-actions.md)
- [程式碼樣式及快速動作](../ide/code-styles-and-quick-actions.md)
- [撰寫及重構程式碼 (C++)](/cpp/ide/writing-and-refactoring-code-cpp)