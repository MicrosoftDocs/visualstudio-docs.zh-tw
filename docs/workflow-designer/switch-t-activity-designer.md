---
title: "交換器&lt;T&gt;活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 69e69ca7453801d6ccc3b5f323035475413721c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="switchlttgt-activity-designer"></a>交換器&lt;T&gt;活動設計工具
<xref:System.Activities.Statements.Switch%601> 活動會評估指定的運算式，並且從關聯索引鍵符合求值結果的活動集合中執行該活動。  
  
 **交換器 < T\>** 活動設計工具用來建立及設定<xref:System.Activities.Statements.Switch%601>中的活動[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]。  
  
## <a name="the-switchtactivity"></a>交換器\<T > 活動  
 <xref:System.Activities.Statements.Switch%601> 活動包含 <xref:System.Activities.Statements.Switch%601.Expression%2A> 與 <xref:System.Activities.Statements.Switch%601.Cases%2A> 的字典。 字典中的每個案例所組成，其中包含一組*金鑰*和做為其對應的活動*值*。 <xref:System.Activities.Statements.Switch%601> 活動會評估 <xref:System.Activities.Statements.Switch%601.Expression%2A>，並與每個索引鍵進行比較。 如果找到符合的項目，則會執行對應的活動。 只會有一個符合的項目，因為根據字典相等比較子所定義的相等類型，字典索引鍵必須是唯一的。 如果找不到符合的項目，就會執行 <xref:System.Activities.Statements.Switch%601.Default%2A> 活動。  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>如何使用參數\<T > 活動設計工具  
 **交換器\<T >**活動設計工具可以在**控制流程**分類的**工具箱**，依序按一下存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)之後它置放於[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]，它會顯示**選取型別**對話方塊，讓使用者指定的泛型型別*T*用於<xref:System.Activities.Statements.Switch%601>活動。 預設值是**Int32**。 一次的泛型型別*T*已選取，**交換器 < T\>** 設計工具是否已加入工作流程設計工具。  
  
 以下是內容的**交換器 < T\>** 設計工具。 這些屬性都可以在屬性方格中編輯。 部分屬性也可以在設計工具介面上編輯。  
  
 下表顯示最為實用的 <xref:System.Activities.Statements.Switch%601> 屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Switch%601> 活動設計工具的易記名稱。 預設值是參數 < Int32\>。 這個值可以在編輯**屬性**視窗或直接在設計工具的標頭。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|指定用於比較案例集合中索引鍵的運算式，以判斷要執行哪一個案例。|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||指定如果找不到符合項目時要執行的活動。 按一下**將活動新增**開啟設計工具上的按鈕**預設**可置放活動的方塊。|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||指定要評估的案例。 若要新增的情況下，按一下**加入新的案例**底部的按鈕**交換器\<T >**設計工具。 按鈕會變成文字方塊 (如果加入這個參數時，選取泛型型別下拉式方塊\<T > 為 String 或 Enum)。 新增中的索引鍵後**值的大小寫** 方塊中，案例區域會展開，且可置放活動，以定義案例的執行邏輯的提示文字 「 在此置放活動 」。|  
  
 只要案例索引鍵不重複，即可加入多個案例。 否則就會顯示一個錯誤對話方塊，表示指定的案例索引鍵已存在，而必須選擇不同的索引鍵。 在**交換器\<T >**設計工具中，只有一個案例區域可以是展開的檢視，一次。 如果案例區域是摺疊檢視狀態，請按一下案例區域將其展開。 請注意，在摺疊的案例中，設計工具會在案例右側顯示活動的顯示名稱 (如果有名稱的話)。 否則，就會顯示**將活動新增**按鈕，按一下即可展開案例並加入活動。  
  
 按一下現有案例的索引鍵，就會從標籤變更為可供編輯案例索引鍵的文字方塊。  
  
 有兩個方法可以刪除案例：  
  
1.  選取該案例，然後將其刪除。  
  
2.  選取案例，以滑鼠右鍵按一下，以顯示內容功能表並選取**刪除**。  
  
 請注意，您必須選取要刪除的案例本身。 選取與刪除案例內的活動僅會刪除活動，而不會刪除案例。  
  
## <a name="see-also"></a>請參閱  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)