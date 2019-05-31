---
title: 計算程式碼度量
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b44f2a36297db3265a3904f1f76596ca6ba0e35
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260478"
---
# <a name="code-metrics-values"></a>程式碼度量值

現代軟體應用程式的複雜度也會增加可靠且易於維護，使程式碼的困難度。 程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 利用程式碼度量，開發人員可以了解哪些類型和/或方法應該修改或進行更徹底的測試。 開發團隊可以找出潛在的風險、 了解專案的目前狀態和追蹤軟體開發過程的進度。

開發人員可以使用 Visual Studio 來產生程式碼度量資料，用來計算的複雜度和維護的 managed 程式碼。 整個解決方案或單一專案，可以產生程式碼度量資料。

如需有關如何在 Visual Studio 中產生程式碼度量資料的資訊，請參閱[How to:產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)。

## <a name="software-measurements"></a>軟體的度量

下列清單顯示的程式碼度量結果，Visual Studio 的計算：

- **可維護性指數**-計算索引值介於 0 到 100，表示相對容易維護的程式碼。 較高的值表示較佳的可維護性。 可用來快速找出問題點，在您的程式碼中設定了色彩標示評等。 綠色的評等是介於 20 到 100 之間，並指出程式碼有良好的可維護性。 黃色的評等是介於 10 到 19，並指出程式碼是可維護性適中。 紅色的評等是介於 0 到 9 的評等，並表示低的可維護性。 如需詳細資訊，請參閱 <<c0> [ 可維護性索引範圍和意義](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/)部落格文章。

- **循環複雜度**-測量程式碼的結構化的複雜度。 它會建立計算的程式流程中不同的程式碼路徑數目。 具有複雜的控制流程的程式需要更多測試來達到良好的程式碼涵蓋範圍，且較不容易維護。 如需詳細資訊，請參閱 <<c0> [ 循環複雜度的維基百科項目](https://wikipedia.org/wiki/Cyclomatic_complexity)。

- **繼承深度**-指出繼承自另一個，一路回溯到基底類別的不同類別的數字。 繼承深度是類似於類別結合程度，因為基底類別中的變更可能會影響任何繼承的類別。 愈高這個數字，更深入的繼承愈高可能會導致中斷的基底類別修改而變更。 繼承深度，較低的值是很好，較高的值不正確。 

- **類別結合程度**-測量透過參數、 區域變數、 傳回型別、 方法呼叫、 泛型或樣板具現化、 基底類別、 介面實作、 外部型別上定義的欄位的唯一類別結合程度和屬性裝飾。 好的軟體設計會要求的型別和方法應該具有高度一致性的特性且低耦合。 結合程度高表示並不容易重複使用，因為其許多其他類型的相互依存性而設計。 如需詳細資訊，請參閱 <<c0> [ 類別結合程度](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/)部落格文章。

- **程式碼行**-指出程式碼行的近似數目。 計數為基礎的 IL 程式碼，因此不精確的原始程式碼檔案中的行數。 將型別或方法嘗試完成太多的工作，並應該分割，可能表示高的計數。 它也可能表示該型別或方法可能很難維護。

   > [!NOTE]
   > [命令列版本](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics)的程式碼度量工具計算實際程式碼行因為它會分析原始程式碼，而不是 IL。

## <a name="anonymous-methods"></a>匿名方法

*匿名方法*是只是一種方法沒有名稱。 匿名方法最常用來做為委派參數傳遞的程式碼區塊。 宣告的成員，例如方法或存取子，匿名方法的度量資訊結果會與宣告方法的成員相關聯。 它們不會呼叫方法的成員與相關聯。

如需有關程式碼度量的匿名方法的處理方式的詳細資訊，請參閱[匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)。

## <a name="generated-code"></a>產生的程式碼

某些軟體工具和編譯器會產生程式碼加入至專案以及專案開發人員看不到或不應該變更。 主要程式碼度量資訊會忽略產生的程式碼時它會計算計量值。 這可讓計量值，以反映功能開發人員可以看到及變更。

Windows Form 的產生程式碼不會進行忽略，因為它是開發人員可以看到及變更的程式碼。

## <a name="next-steps"></a>後續步驟

- [如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)
