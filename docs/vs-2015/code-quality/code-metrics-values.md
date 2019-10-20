---
title: 程式碼度量值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667727"
---
# <a name="code-metrics-values"></a>程式碼度量值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 藉由利用程式碼計量，開發人員可以瞭解哪些類型和（或）方法應該進行返工或更徹底的測試。 開發小組可以識別潛在風險、瞭解專案的目前狀態，以及追蹤軟體發展期間的進度。

## <a name="software-measurements"></a>軟體測量
 下列清單顯示 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 計算的程式碼度量結果：

- 可**維護性索引**–計算介於0和100之間的索引值，表示維護程式碼的相對容易度。 較高的值表示可維護性較佳。 色彩編碼分級可用來快速識別程式碼中的問題點。 綠色的評等介於20到100之間，表示程式碼具有良好的可維護性。 黃色的評等介於10到19之間，表示程式碼是適度維護的。 紅色評等是介於0到9之間的評等，表示可維護性較低。

- **圈**複雜度–測量程式碼的結構複雜度。 它是藉由計算程式流程中不同程式碼路徑的數目來建立。 具有複雜控制流程的程式將需要更多測試，才能達成良好的程式碼涵蓋範圍，而且會比較不容易維護。

    > [!NOTE]
    > 在某些情況下，[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 中方法的圈量複雜度計算與舊版不同。 如需詳細資訊，請參閱針對程式[代碼度量問題進行疑難排解](../code-quality/troubleshooting-code-metrics-issues.md)中的

- **繼承深度**–表示擴充至類別階層架構之類別定義的數目。 階層越深，就越難以瞭解特定方法和欄位的定義或/和重新定義的位置。

- **類別**結合-透過參數、區域變數、傳回型別、方法呼叫、泛型或樣板具現化、基類、介面執行、在外部型別上定義的欄位，以及屬性，測量與唯一類別的結合修飾符. 良好的軟體設計規定型別和方法應該具有高一致性和低耦合。 高結合性表示很容易重複使用和維護的設計，因為它在其他類型上有許多相關性。

- 程式**程式碼**-指出程式碼中的大約行數。 計數是以 IL 程式碼為基礎，因此不是原始程式檔中的確切行數。 非常高的計數可能表示類型或方法正嘗試執行太多工作，因此應該加以分割。 它也可能表示類型或方法可能難以維護。

## <a name="anonymous-methods"></a>匿名方法
 *匿名方法*只是沒有名稱的方法。 匿名方法最常用來傳遞程式碼區塊做為委派參數。 在成員（例如方法或存取子）中宣告之匿名方法的計量結果，會與宣告該方法的成員相關聯。 它們不會與呼叫方法的成員相關聯。

 如需程式碼計量如何處理匿名方法的詳細資訊，請參閱[匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)。

## <a name="generated-code"></a>產生的程式碼
 有些軟體工具和編譯器會產生新增至專案的程式碼，而且專案開發人員不會看到或不應該變更。 大部分的程式碼度量會在計算計量值時，忽略產生的程式碼。 這可讓計量值反映開發人員可以查看和變更的內容。

 系統不會忽略針對 Windows forms 產生的程式碼，因為程式碼是開發人員可以查看和變更的程式碼。

## <a name="see-also"></a>請參閱
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
