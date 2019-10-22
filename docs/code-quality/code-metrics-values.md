---
title: 計算程式碼度量
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db72d5daebd32e53fb690aaa6ad80dc35e68e7a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622428"
---
# <a name="code-metrics-values"></a>程式碼度量值

新式軟體應用程式的複雜性也增加了讓程式碼可靠和維護的難度。 程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 藉由利用程式碼計量，開發人員可以瞭解哪些類型和（或）方法應該進行返工或更徹底的測試。 開發小組可以識別潛在風險、瞭解專案的目前狀態，以及追蹤軟體發展期間的進度。

開發人員可以使用 Visual Studio 來產生程式碼計量資料，以測量其 managed 程式碼的複雜度和維護性。 可以針對整個方案或單一專案產生程式碼計量資料。

如需如何在 Visual Studio 中產生程式碼度量資料的詳細資訊，請參閱[如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)。

## <a name="software-measurements"></a>軟體測量

下列清單顯示 Visual Studio 計算的程式碼度量結果：

- 可**維護性索引**-計算0到100之間的索引值，表示維護程式碼的相對容易度。 較高的值表示可維護性較佳。 色彩編碼分級可用來快速識別程式碼中的問題點。 綠色的評等介於20到100之間，表示程式碼具有良好的可維護性。 黃色的評等介於10到19之間，表示程式碼是適度維護的。 紅色評等是介於0到9之間的評等，表示可維護性較低。 如需詳細資訊，請參閱可[維護性索引範圍和意義](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/)blog 文章。

- **圈**複雜度-測量程式碼的結構複雜度。 它是藉由計算程式流程中不同程式碼路徑的數目來建立。 具有複雜控制流程的程式需要進行更多測試，才能達成良好的程式碼涵蓋範圍，且維護效率較低。 如需詳細資訊，請參閱「[圈複雜度」的維琪百科專案](https://wikipedia.org/wiki/Cyclomatic_complexity)。

- **繼承深度**-指出繼承自另一個類別的不同類別數目，一直回到基類。 繼承深度與類別結合性相似之處在于，基底類別中的變更可能會影響其繼承的任何類別。 這個數位愈大，繼承越深入，而基類修改的可能性也會導致中斷性變更。 如需繼承的深度，較低的值是良好的，而高值則不正確。

- **類別**結合-透過參數、區域變數、傳回型別、方法呼叫、泛型或樣板具現化、基類、介面執行、外部型別上定義的欄位和屬性，測量與唯一類別的結合修飾符. 良好的軟體設計規定型別和方法應該具有高一致性和低耦合。 高結合性表示很容易重複使用和維護的設計，因為它在其他類型上有許多相關性。 如需詳細資訊，請參閱[類別](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/)結合 blog 文章。

- 程式**程式碼**-指出程式碼中的大約行數。 計數是以 IL 程式碼為基礎，因此不是原始程式檔中的確切行數。 較高的計數可能表示類型或方法嘗試執行太多工作，因此應該加以分割。 它也可能表示類型或方法可能難以維護。

   > [!NOTE]
   > [程式碼計量] 工具的[命令列版本](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics)會計算實際的程式程式碼，因為它會分析原始程式碼，而不是 IL。

## <a name="anonymous-methods"></a>匿名方法

*匿名方法*只是沒有名稱的方法。 匿名方法最常用來傳遞程式碼區塊做為委派參數。 在成員（例如方法或存取子）中宣告之匿名方法的程式碼度量結果，會與宣告該方法的成員相關聯。 它們不會與呼叫方法的成員相關聯。

## <a name="generated-code"></a>產生的程式碼

有些軟體工具和編譯器會產生新增至專案的程式碼，而且專案開發人員不會看到或不應該變更。 大部分的程式碼度量會在計算計量值時，忽略產生的程式碼。 這可讓計量值反映開發人員可以查看和變更的內容。

不會忽略針對 Windows Forms 產生的程式碼，因為程式碼是開發人員可以查看和變更的程式碼。

## <a name="next-steps"></a>後續步驟

- [如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)
