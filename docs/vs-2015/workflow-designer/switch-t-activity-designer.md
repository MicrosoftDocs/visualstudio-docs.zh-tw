---
title: 切換 &lt;T &gt; 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb6d4eb189b75d6e401bca0cfe50a71081760478
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660106"
---
# <a name="switchlttgt-activity-designer"></a>切換 &lt;T &gt; 活動設計工具
<xref:System.Activities.Statements.Switch%601> 活動會評估指定的運算式，並且從關聯索引鍵符合求值結果的活動集合中執行該活動。

 **參數 \<T >** 活動設計工具會用來建立和設定 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中的 <xref:System.Activities.Statements.Switch%601> 活動。

## <a name="the-switchtactivity"></a>切換 \<T > 活動
 <xref:System.Activities.Statements.Switch%601> 活動包含 <xref:System.Activities.Statements.Switch%601.Expression%2A> 與 <xref:System.Activities.Statements.Switch%601.Cases%2A> 的字典。 字典中的每個案例都是由一個配對組成，其中包含一個索引*鍵*和一個活動，做為其對應的*值*。 <xref:System.Activities.Statements.Switch%601> 活動會評估 <xref:System.Activities.Statements.Switch%601.Expression%2A>，並與每個索引鍵進行比較。 如果找到符合的項目，則會執行對應的活動。 只會有一個符合的項目，因為根據字典相等比較子所定義的相等類型，字典索引鍵必須是唯一的。 如果找不到符合的項目，就會執行 <xref:System.Activities.Statements.Switch%601.Default%2A> 活動。

## <a name="how-to-use-the-switcht-activity-designer"></a>如何使用參數 \<T > 活動設計工具
 [**切換 \<T >** ] 活動設計工具位於 [**工具箱**] 的 [**控制流程**] 分類中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 上的 [**工具箱**] 索引標籤（也可以從視圖選取 [**工具列**]）。功能表，或按 CTRL + ALT + X）。將它放入 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 之後，它會顯示 [**選取類型**] 對話方塊，讓使用者指定用於 1 活動中的泛型型別*t* 。 預設值為**Int32**。 選取泛型型別*T*之後，就會在工作流程設計工具中加入**切換 \<T >** 設計工具。

 以下是**參數 \<T >** 設計工具的屬性。 這些屬性都可以在屬性方格中編輯。 部分屬性也可以在設計工具介面上編輯。

 下表顯示最為實用的 <xref:System.Activities.Statements.Switch%601> 屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Switch%601> 活動設計工具的易記名稱。 預設值為 Switch \<Int32 >。 此值可在 [**屬性**] 視窗中編輯，或直接在設計工具標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|指定用於比較案例集合中索引鍵的運算式，以判斷要執行哪一個案例。|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||指定如果找不到符合項目時要執行的活動。 按一下設計工具上的 [**加入活動**] 按鈕，開啟可卸載活動的**預設**方塊。|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||指定要評估的案例。 若要加入案例，請按一下 [**切換 \<T >** 設計工具] 底部的 [**加入新案例**] 按鈕。 按鈕會變成文字方塊（如果在加入參數時選取的泛型型別 \<T > 為 String 或 Enum），則會變更為下拉式方塊。 在 [ **case 值**] 方塊中加入索引鍵後，案例區域會展開，並在提示文字「卸載活動于此處」處卸載活動，以定義案例的執行邏輯。|

 只要案例索引鍵不重複，即可加入多個案例。 否則就會顯示一個錯誤對話方塊，表示指定的案例索引鍵已存在，而必須選擇不同的索引鍵。 在 [**切換 \<T >** 設計師] 中，一次只能有一個案例區域在展開視圖中。 如果案例區域是摺疊檢視狀態，請按一下案例區域將其展開。 請注意，在摺疊的案例中，設計工具會在案例右側顯示活動的顯示名稱 (如果有名稱的話)。 否則，它會顯示 [**加入活動**] 按鈕，以在您按一下它並讓您新增活動時展開案例。

 按一下現有案例的索引鍵，就會從標籤變更為可供編輯案例索引鍵的文字方塊。

 有兩個方法可以刪除案例：

1. 選取該案例，然後將其刪除。

2. 選取案例，按一下滑鼠右鍵以顯示內容功能表，然後選取 [**刪除**]。

   請注意，您必須選取要刪除的案例本身。 選取與刪除案例內的活動僅會刪除活動，而不會刪除案例。

## <a name="see-also"></a>請參閱
 [控制流程](../workflow-designer/control-flow-activity-designers.md)