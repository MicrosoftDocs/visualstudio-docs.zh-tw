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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b216e89e6a04fb38537f9c45336d07cf6df4abdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671276"
---
# <a name="responding-to-and-propagating-changes"></a>回應及傳播變更
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

建立、刪除或更新專案時，您可以撰寫程式碼來將變更傳播到模型的其他部分，或寫入外部資源，例如檔案、資料庫或其他元件。

## <a name="in-this-section"></a>本章節內容
 依照下列順序，將這些技巧視為指導方針：

|稱為|案例|如需詳細資訊|
|---------------|---------------|--------------------------|
|定義匯出定義域屬性。|網域屬性，其值是從模型中的其他屬性計算而來。 例如，這是相關元素的價格總和。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|
|定義自訂的儲存網域屬性。|儲存在模型的其他部分或外部的網域屬性。 例如，您可以將運算式字串剖析成模型中的樹狀結構。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|
|覆寫變更處理常式，例如 OnValueChanging 和 OnDeleting|讓不同的元素保持同步，並讓外部值與模型保持同步。<br /><br /> 將值限制為定義的範圍。<br /><br /> 緊接在屬性值和其他變更之前和之後呼叫。 您可以藉由擲回例外狀況來終止變更。|[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)|
|規則|您可以定義在發生變更的交易結束之前，已排入佇列等候執行的規則。 它們不會在復原或重做時執行。 使用它們讓存放區的一部分與另一個部分保持同步。|[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)|
|儲存事件|模型存放區會提供事件的通知，例如新增或刪除專案或連結，或變更屬性的值。 這個事件也會在復原和重做時執行。 使用存放區事件來更新不在存放區中的值。|[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET 事件|圖形具有回應滑鼠點按和其他手勢的事件處理常式。 您必須為每個物件註冊這些事件。 註冊通常會在 InitializeInstanceResources 的覆寫中完成，而且必須針對每個元素完成。<br /><br /> 這些事件通常發生在交易外。|[如何：攔截圖案或 Decorator 上的點選](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|界限規則|界限規則是專門用來限制圖形的範圍。|[BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|選取規則|選取規則會特別限制使用者可選取的專案。|[如何：存取及限制目前的選取範圍](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|使用陰影、箭頭、色彩和線條寬度和樣式等形狀和接點的功能，指出模型元素的狀態。|[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**比較規則和儲存事件**
 當模型中發生變更時，會執行變更通告、規則和事件。

 規則通常會套用至已發生變更的結束交易，而事件會在認可交易中的變更之後套用。

 使用存放區事件來同步處理模型與存放區外的物件，以及維護存放區內一致性的規則。

- **建立自訂規則**您可以從抽象規則建立自訂規則做為衍生類別。 您也必須通知架構有關自訂規則的資訊。 如需詳細資訊，請參閱[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

- **訂閱事件**您必須先建立事件處理常式和委派，才能訂閱事件。 然後使用 <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>property 來訂閱事件。 如需詳細資訊，請參閱[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

- 復原**變更**當您復原交易時，會引發事件，但不會套用規則。 如果規則變更某個值，而您又復原該變更，則在復原動作期間，值會重設為原始值。 當引發事件時，您必須手動將值變更回其原始值。 若要深入瞭解 transactons 和復原，請參閱[如何：使用交易來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。

- **將事件引數傳遞至規則和事件**事件和規則都會傳遞 `EventArgs` 參數，其中包含模型變更的相關資訊。

## <a name="see-also"></a>請參閱
 [如何：攔截圖形上的按一下或](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)裝飾專案[撰寫程式碼，以自訂域特定語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
