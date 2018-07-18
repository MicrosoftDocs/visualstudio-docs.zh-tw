---
title: 工作流程設計工具-交換器<T>活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afa5932ebfaea1e0a7f61997c26e95226ed51b1d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758012"
---
# <a name="switcht-activity-designer"></a>交換器\<T > 活動設計工具

<xref:System.Activities.Statements.Switch%601> 活動會評估指定的運算式，並且從關聯索引鍵符合求值結果的活動集合中執行該活動。

**交換器 < T\>** 活動設計工具會用來建立及設定<xref:System.Activities.Statements.Switch%601>Workflow Designer 中的活動。

## <a name="the-switchtactivity"></a>切換\<T > 活動

<xref:System.Activities.Statements.Switch%601> 活動包含 <xref:System.Activities.Statements.Switch%601.Expression%2A> 與 <xref:System.Activities.Statements.Switch%601.Cases%2A> 的字典。 在字典中的每個案例所組成，其中包含一組*金鑰*和 做為其對應的活動*值*。 <xref:System.Activities.Statements.Switch%601> 活動會評估 <xref:System.Activities.Statements.Switch%601.Expression%2A>，並與每個索引鍵進行比較。 如果找到符合的項目，則會執行對應的活動。 只會有一個符合的項目，因為根據字典相等比較子所定義的相等類型，字典索引鍵必須是唯一的。 如果找不到符合的項目，就會執行 <xref:System.Activities.Statements.Switch%601.Default%2A> 活動。

## <a name="how-to-use-the-switcht-activity-designer"></a>如何使用參數\<T > 活動設計工具

存取**交換器\<T >** 中的活動設計工具**控制流程**分類**工具箱**。 之後放入工作流程設計工具，它會顯示**選取型別**對話方塊，供使用者指定的泛型型別*T*用於<xref:System.Activities.Statements.Switch%601>活動。 預設值是**Int32**。 一次的泛型型別*T*已選取，**交換器 < T\>** 設計工具就會加入至工作流程設計工具。

以下是的內容**交換器 < T\>** 設計工具。 這些屬性都可以在屬性方格中編輯。 部分屬性也可以在設計工具介面上編輯。

下表顯示最為實用的 <xref:System.Activities.Statements.Switch%601> 屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Switch%601> 活動設計工具的易記名稱。 預設值是 Switch < Int32\>。 值可以在中編輯**屬性**視窗或直接在設計工具的標頭。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|指定用於比較案例集合中索引鍵的運算式，以判斷要執行哪一個案例。|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||指定如果找不到符合項目時要執行的活動。 按一下 **將活動新增**以開啟設計工具上的按鈕**預設**可以卸除活動的方塊。|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||指定要評估的案例。 若要新增的情況下，按一下**新增新的案例**底部的按鈕**交換器\<T >** 設計工具。 按鈕會變成文字方塊 (如果時新增參數的泛型型別所選取的下拉式方塊\<T > 為 String 或 Enum)。 新增中的索引鍵之後**Case 值** 方塊中，案例區域會展開，且活動可以卸除其中提示文字 「 在此置放活動 」，以定義案例的執行邏輯。|

只要案例索引鍵不重複，即可加入多個案例。 否則就會顯示一個錯誤對話方塊，表示指定的案例索引鍵已存在，而必須選擇不同的索引鍵。 在 **交換器\<T >** 設計工具中，只有一個案例區域可以是一次展開之檢視中。 如果案例區域是摺疊檢視狀態，請按一下案例區域將其展開。 請注意，在摺疊的案例中，設計工具會在案例右側顯示活動的顯示名稱 (如果有名稱的話)。 否則，它會顯示**將活動新增**展開案例，如果您按一下它，並讓您將活動新增的按鈕。

按一下現有案例的索引鍵，就會從標籤變更為可供編輯案例索引鍵的文字方塊。

有兩個方法可以刪除案例：

- 選取該案例，然後將其刪除。

- 選取案例中，按一下滑鼠右鍵以顯示操作功能表，然後選取**刪除**。

請注意，您必須選取要刪除的案例本身。 選取與刪除案例內的活動僅會刪除活動，而不會刪除案例。

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)