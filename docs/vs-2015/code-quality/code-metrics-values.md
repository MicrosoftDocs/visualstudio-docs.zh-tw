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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667727"
---
# <a name="code-metrics-values"></a>程式碼度量值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 藉由利用程式碼計量，開發人員可以瞭解哪些類型和/或方法應該要修改或更徹底測試。 開發小組可以找出潛在的風險、瞭解專案的目前狀態，以及追蹤軟體發展期間的進度。

## <a name="software-measurements"></a>軟體度量
 下列清單顯示計算的程式碼度量結果 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ：

- 可**維護性索引**–計算介於0和100之間的索引值，表示維護程式碼的相對便利性。 高價值表示較佳的可維護性。 色彩編碼分級可以用來快速找出程式碼中的問題點。 綠色的評等介於20到100之間，表示程式碼具有良好的可維護性。 黃色的評等介於10和19之間，表示程式碼為適度維護。 紅色評等是介於0到9之間的評等，表示低維護性。

- 迴圈**複雜度**–測量程式碼的結構複雜度。 它是藉由計算程式流程中的不同程式碼路徑數目來建立。 具有複雜控制流程的程式將需要更多測試，才能達到良好的程式碼涵蓋範圍，且會比較不容易維護。

    > [!NOTE]
    > 在某些情況下，中方法的迴圈複雜度計算 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 與舊版不同。 如需詳細資訊，請參閱針對程式 [代碼計量問題進行疑難排解](../code-quality/troubleshooting-code-metrics-issues.md)的「Visual Studio 2010 程式碼複雜性計算」一節中的變更。

- **繼承深度** -表示延伸至類別階層根目錄的類別定義數目。 階層越深層越難理解特定方法和欄位的定義或/或重新定義。

- **類別** 結合–透過參數、區域變數、傳回型別、方法呼叫、泛型或樣板具現化、基類、介面實現、在外部類型上定義的欄位，以及屬性裝飾，來測量與唯一類別的結合。 良好的軟體設計會指出類型和方法應該具有高一致性和低耦合。 高度結合表示很難重複使用和維護的設計，因為它在其他類型上有許多相關性。

- 程式**程式碼**-指出程式碼中大約的行數。 計數是以 IL 程式碼為基礎，因此不是原始程式碼檔中確切的行數。 很高的計數可能表示類型或方法正在嘗試執行太多工作，而且應該進行分割。 這也可能表示類型或方法可能難以維護。

## <a name="anonymous-methods"></a>匿名方法
 *匿名方法*只是沒有名稱的方法。 匿名方法最常用來將程式碼區塊當做委派參數傳遞。 在成員中宣告的匿名方法（例如方法或存取子）的計量結果，會與宣告方法的成員相關聯。 它們不會與呼叫方法的成員相關聯。

 如需程式碼計量如何處理匿名方法的詳細資訊，請參閱 [匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)。

## <a name="generated-code"></a>產生的程式碼
 有些軟體工具和編譯器會產生加入至專案的程式碼，而專案開發人員不會看到或不應變更。 大部分情況下，程式碼度量會在計算計量值時忽略產生的程式碼。 這可讓計量值反映開發人員可查看和變更的內容。

 不會忽略針對 Windows form 產生的程式碼，因為這是開發人員可以看到及變更的程式碼。

## <a name="see-also"></a>另請參閱
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
