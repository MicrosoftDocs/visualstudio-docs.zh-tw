---
title: 回應，且將變更傳播 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f814cc9ca963b59217dc486539d22f42f487a3db
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="responding-to-and-propagating-changes"></a>回應及傳播變更
當建立、 刪除或更新項目時，您可以撰寫傳播變更給模型的其他組件或外部的資源，例如檔案、 資料庫或其他元件的程式碼。  
  
## <a name="in-this-section"></a>本節內容  
 一般來說，請考慮下列技術順序如下：  
  
|技術|案例|如需詳細資訊|  
|---------------|---------------|--------------------------|  
|定義導出的網域屬性。|網域屬性，其值從模型中的其他屬性計算。 例如，價格的相關元素的加總價格。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|  
|定義的自訂儲存體網域屬性。|網域屬性，儲存在模型或外部的其他部分。 例如，您無法剖析運算式字串為模型中的樹狀目錄。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|  
|覆寫 OnValueChanging 等 OnDeleting 變更處理常式|保持同步，不同的項目，外部值與保持同步模型。<br /><br /> 限制值來定義的範圍。<br /><br /> 呼叫之前和之後屬性值和其他變更。 您可以藉由擲回例外狀況終止變更。|[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)|  
|規則|您可以定義佇列中等待變更發生在交易結束之前執行的規則。 它們不會在復原或重做上執行。 您可以使用它們來保留存放區的一組件與另一個同步處理。|[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)|  
|儲存事件|模型存放區，提供通知的事件，例如加入或刪除項目或連結，或變更屬性的值。 事件也會復原和取消復原上執行。 您可以使用存放區事件更新不在存放區中的值。|[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET 事件|圖形有回應滑鼠點選與其他筆勢的事件處理常式。 您必須註冊這些事件中的每個物件。 註冊通常是 InitializeInstanceResources，覆寫中，且必須進行的每個項目。<br /><br /> 這些事件通常發生於外部交易。|[如何：攔截圖案或 Decorator 上的點選](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|範圍規則|範圍規則是特別用來限制圖形的界限。|[BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|選取規則|選取規則特別限制使用者可以選取的項目。|[如何：存取及限制目前的選取範圍](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|表示使用的圖形和連接器陰影、 箭頭、 色彩和線條寬度和樣式等功能的模型項目狀態。|[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**比較規則與事件存放區**  
 在模型中發生變更時，會執行變更 notifiers、 規則和事件。  
  
 規則通常會套用在一般交易中發生變更，並認可交易中的變更之後，事件會套用。  
  
 使用存放區事件來同步處理的模型使用外部存放區和規則，以維護一致性存放區中的物件。  
  
-   **建立自訂規則**您為抽象的規則從衍生類別中建立自訂規則。 您也必須通知有關的自訂規則的架構。 如需詳細資訊，請參閱[規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
-   **訂閱事件**可以訂閱事件之前，建立事件處理常式和委派。 然後使用<xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>訂閱事件的屬性。 如需詳細資訊，請參閱[事件處理常式傳播變更外部模型](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
-   **復原變更**時復原交易，會引發事件，但是不會套用規則。 如果規則會將值變更，您可以復原該變更值會重設原始的值在復原動作。 事件引發時，您必須手動變更此值設回其原始值。 若要深入了解 transactons 和復原，請參閱[How to： 使用異動來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
-   **事件引數傳遞至規則和事件**這兩個事件和傳遞規則`EventArgs`參數的相關資訊的模型變更。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 攔截按一下圖形或裝飾項目](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)