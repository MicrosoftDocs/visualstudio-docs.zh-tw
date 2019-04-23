---
title: 回應及傳播變更 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9838e934421e619c85f348052fbe589288391c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104716"
---
# <a name="responding-to-and-propagating-changes"></a>回應及傳播變更
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當建立、 刪除或更新項目時，您可以撰寫會傳播變更的其他部分的模型或外部的資源，例如檔案、 資料庫或其他元件的程式碼。  
  
## <a name="in-this-section"></a>本節內容  
 做為指導方針，請考慮下列技術順序如下：  
  
|技術|案例|如需詳細資訊|  
|---------------|---------------|--------------------------|  
|定義導出的網域屬性。|網域屬性，其值會計算從模型中的其他屬性。 例如，價格是相關項目的價格總和。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|  
|定義自訂儲存網域屬性。|網域屬性，儲存在模型或外部的其他部分。 比方說，您可以剖析的運算式字串到模型中的樹狀結構。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|  
|覆寫 OnValueChanging 等 OnDeleting 變更處理常式|保留不同的項目進行同步處理，並讓外部值與模型保持同步。<br /><br /> 限制值來定義的範圍。<br /><br /> 呼叫前後立即屬性值和其他變更。 您可以藉由擲回例外狀況終止變更。|[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)|  
|規則|您可以定義佇列中等待執行的變更發生在交易結束之前的規則。 它們不會在復原或重做上執行。 您可以使用它們來持續存放區的一組件與另一個的同步處理。|[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)|  
|存放區事件|模型存放區提供通知的事件，例如加入或刪除項目或連結，或變更屬性的值。 事件也會在復原與取消復原上執行。 您可以使用存放區事件更新不在存放區中的值。|[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET 事件|圖形會有回應滑鼠點按和其他筆勢的事件處理常式。 您必須註冊這些事件的每個物件。 註冊通常是 InitializeInstanceResources，覆寫，且必須以每個項目。<br /><br /> 這些事件通常發生於交易外部的。|[如何：攔截圖形或裝飾項目上的點選](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|範圍規則|繫結規則，特別用於限制圖形的界限。|[BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|選取規則|選取規則特別限制使用者可以選取。|[如何：存取及限制目前的選取範圍](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|表示使用的圖案和接點陰影、 線條、 色彩和線條寬度和樣式等功能的模型項目的狀態。|[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**比較的規則和存放區事件**  
 在模型中發生變更時，會執行變更 notifiers、 規則和事件。  
  
 規則通常會套用在其中發生的變更，結束交易並認可交易中的變更之後，會套用事件。  
  
 若要使用外部存放區和規則，以維護一致性的存放區中的物件同步處理的模型使用存放區事件。  
  
- **建立自訂規則**您建立自訂規則做為衍生的類別，從抽象的規則。 您也必須通知的自訂規則相關的架構。 如需詳細資訊，請參閱 <<c0> [ 規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
- **訂閱事件**可以訂閱事件之前，請建立事件處理常式和委派。 然後使用<xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>訂閱事件的屬性。 如需詳細資訊，請參閱 <<c0> [ 事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
- **正在恢復變更**時將交易復原，會引發事件，但不是會套用規則。 如果規則變更的值，而且復原這項變更，值會重設為原始值期間復原動作。 當引發事件時，您必須手動變更此值設回其原始值。 若要深入了解 transactons 和復原，請參閱[How to:使用異動更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
- **傳遞規則和事件的事件引數**這兩個事件和傳遞規則`EventArgs`參數，其資訊的模型變更。  
  
## <a name="see-also"></a>另請參閱  
 [如何：攔截圖案或 Decorator 上的](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
