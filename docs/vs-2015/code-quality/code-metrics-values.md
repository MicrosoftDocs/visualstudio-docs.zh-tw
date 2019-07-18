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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f103a1239996e1f68fb6dae7a9f0a41f55ad858e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437093"
---
# <a name="code-metrics-values"></a>程式碼度量值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 利用程式碼度量，開發人員可以了解哪些類型和/或方法應該修改或進行更徹底的測試。 開發團隊可以找出潛在的風險、 了解專案的目前狀態和追蹤軟體開發過程的進度。  
  
## <a name="software-measurements"></a>軟體的度量  
 下列清單會顯示程式碼度量結果[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]計算：  
  
- **可維護性指數**– 計算索引值介於 0 到 100，表示相對容易維護的程式碼。 較高的值表示較佳的可維護性。 可用來快速找出問題點，在您的程式碼中設定了色彩標示評等。 綠色的評等是介於 20 到 100 之間，並指出程式碼有良好的可維護性。 黃色的評等是介於 10 到 19，並指出程式碼是可維護性適中。 紅色的評等是介於 0 到 9 的評等，並表示低的可維護性。  
  
- **循環複雜度**– 測量程式碼的結構化的複雜度。 它會建立計算的程式流程中不同的程式碼路徑數目。 具有複雜的控制流程的程式將會需要更多測試來達到良好的程式碼涵蓋範圍，因此比較不容易維護。  
  
    > [!NOTE]
    > 在某些情況下，循環複雜度中方法的計算[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]與舊版不同。 如需詳細資訊，請參閱 「 變更在 Visual Studio 2010 程式碼複雜度計算區段 」 的[疑難排解程式碼度量問題](../code-quality/troubleshooting-code-metrics-issues.md)。  
  
- **繼承深度**– 指出類別階層的根擴充的類別定義的數目。 更深的階層更加困難可能了解特定的方法和欄位定義或 / 及重新定義。  
  
- **類別結合程度**– 測量透過參數、 區域變數、 傳回型別、 方法呼叫、 泛型或樣板具現化、 基底類別、 介面實作、 外部型別上定義的欄位的唯一類別結合程度和屬性裝飾。 好的軟體設計會要求的型別和方法應該具有高度一致性的特性且低耦合。 結合程度高表示並不容易重複使用，因為其許多其他類型的相互依存性而設計。  
  
- **程式碼行**-指出程式碼行的近似數目。 計數為基礎的 IL 程式碼，因此不精確的原始程式碼檔案中的行數。 將型別或方法嘗試完成太多的工作，並應該分割，可能表示非常高的計數。 它也可能表示該型別或方法可能很難維護。  
  
## <a name="anonymous-methods"></a>匿名方法  
 *匿名方法*是只是一種方法沒有名稱。 匿名方法最常用來做為委派參數傳遞的程式碼區塊。 宣告的成員，例如方法或存取子，匿名方法的度量資訊結果會與宣告方法的成員相關聯。 它們不會呼叫方法的成員與相關聯。  
  
 如需有關程式碼度量的匿名方法的處理方式的詳細資訊，請參閱[匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)。  
  
## <a name="generated-code"></a>產生的程式碼  
 某些軟體工具和編譯器會產生程式碼加入至專案以及專案開發人員看不到或不應該變更。 主要程式碼度量資訊會忽略產生的程式碼時它會計算計量值。 這可讓計量值，以反映功能開發人員可以看到及變更。  
  
 Windows form 的產生程式碼不會進行忽略，因為它是開發人員可以看到及變更的程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
