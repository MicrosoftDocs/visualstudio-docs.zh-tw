---
title: 回應及傳播變更
description: 瞭解當元素建立、刪除或更新時，您可以撰寫程式碼，將變更傳播至模型的其他部分或外部資源。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e44def032854e46b00638cff77c8bea91eb0f09
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360608"
---
# <a name="respond-to-and-propagate-changes"></a>回應及傳播變更

當元素建立、刪除或更新時，您可以撰寫程式碼，將變更傳播到模型的其他部分，或寫入外部資源（例如檔案、資料庫或其他元件）。

## <a name="reference"></a>參考

作為指導方針，請以下列順序考慮這些技術：

|技巧|案例|取得詳細資訊|
|-|-|-|
|定義匯出的定義域屬性。|定義域屬性，其值是從模型中的其他屬性計算而來。 例如，價格是相關元素的價格總和。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|
|定義自訂儲存網域屬性。|儲存在模型的其他部分或外部的網域屬性。 例如，您可以將運算式字串剖析為模型中的樹狀結構。|[計算及自訂的儲存區屬性](../modeling/calculated-and-custom-storage-properties.md)|
|覆寫變更處理常式，例如 OnValueChanging 和 OnDeleting|讓不同的元素保持同步，並讓外部值與模型保持同步。<br /><br /> 將值限制為定義的範圍。<br /><br /> 緊接在屬性值和其他變更之前和之後呼叫。 您可以藉由擲回例外狀況來終止變更。|[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)|
|規則|您可以定義在發生變更的交易結束之前，將執行排入佇列的規則。 它們不會在復原或重做時執行。 使用它們可讓存放區的其中一個部分與另一個部分進行同步處理。|[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)|
|儲存事件|模型存放區會提供事件的通知，例如新增或刪除專案或連結，或變更屬性的值。 此事件也會在復原和重做時執行。 使用存放區事件來更新不在存放區中的值。|[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET 事件|圖形具有可回應滑鼠點擊和其他手勢的事件處理常式。 您必須為每個物件註冊這些事件。 註冊通常是在 InitializeInstanceResources 覆寫中完成，而且必須針對每個元素完成。<br /><br /> 這些事件通常會發生在交易之外。|[如何：攔截圖案或 Decorator 上的點選](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|界限規則|界限規則專門用來限制圖形的界限。|[BoundsRules 限制圖案位置和大小](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|選取規則|選取規則會特別限制使用者可選取的專案。|[如何：存取及限制目前的選取範圍](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|使用圖形和接點的功能（例如陰影、箭頭、色彩和線條寬度和樣式），指出模型專案的狀態。|[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>比較規則和儲存事件

當模型中發生變更時，會執行變更的觸發、規則和事件。

規則通常會在發生變更的結束交易中套用，並且在認可交易中的變更之後套用事件。

使用存放區事件，將模型與存放區外的物件進行同步處理，並使用規則來維護存放區中的一致性。

- **建立自訂規則** 您可以建立自訂規則，做為抽象規則的衍生類別。 您也必須通知架構有關自訂規則。 如需詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。

- **訂閱事件** 在訂閱事件之前，請先建立事件處理常式和委派。 然後使用 <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> 屬性來訂閱事件。 如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。

- 復原 **變更** 當您復原交易時，會引發事件，但不會套用規則。 如果規則變更某個值，而您復原該變更，則在復原動作期間，值會重設為原始值。 引發事件時，您必須手動將值變更回其原始值。 若要深入瞭解交易和復原，請參閱 [如何：使用交易來更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。

- **將事件引數傳遞至規則和事件** 事件和規則都會傳遞一個 `EventArgs` 參數，其中包含模型變更方式的相關資訊。

## <a name="see-also"></a>請參閱

- [如何：攔截圖案或 Decorator 上的點選](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [撰寫程式碼以自訂 Domain-Specific 語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)