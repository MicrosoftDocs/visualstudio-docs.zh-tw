---
title: 計算程式碼度量
ms.date: 11/02/2018
description: 瞭解迴圈複雜度、類別結合，以及其他 Visual Studio 程式碼度量。 瞭解計量如何追蹤開發進度及找出風險。
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f843df01059adef3a94bb46501e4e75bd67d5a7
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069483"
---
# <a name="code-metrics-values"></a>程式碼度量值

新式軟體應用程式增加的複雜度也會提高使程式碼可靠且可維護的困難。 程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 藉由利用程式碼計量，開發人員可以瞭解哪些類型和/或方法應該要修改或更徹底測試。 開發小組可以找出潛在的風險、瞭解專案的目前狀態，以及追蹤軟體發展期間的進度。

開發人員可以使用 Visual Studio 來產生程式碼度量資料，以測量其 managed 程式碼的複雜性和可維護性。 您可以針對整個方案或單一專案產生程式碼度量資料。

如需有關如何在 Visual Studio 中產生程式碼度量資料的詳細資訊，請參閱 [如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)。

## <a name="software-measurements"></a>軟體度量

下列清單顯示 Visual Studio 計算的程式碼度量結果：

- 可 **維護性索引**-計算介於0和100之間的索引值，表示維護程式碼的相對便利性。 高價值表示較佳的可維護性。 色彩編碼分級可以用來快速找出程式碼中的問題點。 綠色的評等介於20到100之間，表示程式碼具有良好的可維護性。 黃色的評等介於10和19之間，表示程式碼為適度維護。 紅色評等是介於0到9之間的評等，表示低維護性。 如需詳細資訊，請參閱可 [維護性索引範圍和意義](code-metrics-maintainability-index-range-and-meaning.md)。

- 迴圈 **複雜度**-測量程式碼的結構複雜度。 它是藉由計算程式流程中的不同程式碼路徑數目來建立。 具有複雜控制流程的程式需要進行更多測試，才能達到良好的程式碼涵蓋範圍，且較不容易維護。 如需詳細資訊，請參閱 [適用于圈複雜度的維琪百科專案](https://wikipedia.org/wiki/Cyclomatic_complexity)。

- **繼承深度** -表示繼承自另一個類別的不同類別數目，並返回基類。 繼承深度類似于類別結合，因為基類的變更可能會影響其任何繼承的類別。 這個數位愈大，繼承越深入，而基類修改可能會導致中斷性變更。 針對繼承深度，較低的值是良好的，且較高的值是不正確的。

- **類別** 結合-透過參數、區域變數、傳回型別、方法呼叫、泛型或樣板具現化、基類、介面實現、在外部類型上定義的欄位，以及屬性裝飾，來測量與唯一類別的結合。 良好的軟體設計會指出類型和方法應該具有高一致性和低耦合。 高度結合表示很難重複使用和維護的設計，因為它在其他類型上有許多相關性。 如需詳細資訊，請參閱 [類別](code-metrics-class-coupling.md)結合性。

::: moniker range=">=vs-2019"

- **原始程式碼的行** 數-指出原始程式檔中出現的原始程式程式碼確切數目，包括空白行。 從 Visual Studio 2019 16.4 版和 CodeAnalysis (2.9.5) 開始提供此計量。

- **可執行檔程式碼** 的程式碼-指出大約數目的可執行程式程式碼或作業。 這是可執行程式碼中的作業數目計數。 從 Visual Studio 2019 16.4 版和 CodeAnalysis (2.9.5) 開始提供此計量。 此值通常與先前的計量（程式 **程式碼**）相近，這是舊版模式中使用的 MSIL 指令型計量。
::: moniker-end
::: moniker range="vs-2017"

- 程式 **程式碼**-指出程式碼中大約的行數。 計數是以 IL 程式碼為基礎，因此不是原始程式碼檔中確切的行數。 高計數可能表示類型或方法正在嘗試執行太多工作，並應進行分割。 這也可能表示類型或方法可能難以維護。

   > [!NOTE]
   > 程式碼計量工具的 [命令列版本](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) 會計算程式碼的實際程式程式碼，因為它會分析原始程式碼而不是 IL。
::: moniker-end

## <a name="anonymous-methods"></a>匿名方法

*匿名方法* 只是沒有名稱的方法。 匿名方法最常用來將程式碼區塊當做委派參數傳遞。 在成員中宣告的匿名方法（例如方法或存取子）的程式碼度量結果，會與宣告方法的成員相關聯。 它們不會與呼叫方法的成員相關聯。

## <a name="generated-code"></a>產生的程式碼

有些軟體工具和編譯器會產生加入至專案的程式碼，而專案開發人員不會看到或不應變更。 大部分情況下，程式碼度量會在計算計量值時忽略產生的程式碼。 這可讓計量值反映開發人員可查看和變更的內容。

不會忽略針對 Windows Forms 產生的程式碼，因為這是開發人員可以看到及變更的程式碼。

## <a name="next-steps"></a>後續步驟

- [How to：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)