---
title: 規則集編輯器對話方塊（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846319"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>規則集編輯器對話方塊 (舊版)
本主題描述如何在舊版 [!INCLUDE[wfd1](../includes/wfd1-md.md)]中使用 [**規則集編輯器**] 對話方塊。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

 [**規則集編輯器**] 對話方塊是用來建立和修改[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)規則集，這些規則集會序列化為 rules 檔案。

> [!NOTE]
> 如果您想要使用**具有編碼的 XML 編輯器**來開啟 rules 檔案，您必須先關閉工作流程或活動的關聯設計工具視窗。

 如需如何存取 [**規則集編輯器**] 對話方塊的相關資訊，請參閱[如何：建立 PolicyActivity 規則集（舊版）](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)。

> [!WARNING]
> 舊版 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 的規則編輯器，它所針對的 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 不支援多重目標。

 下表描述 [**規則集編輯器**] 對話方塊的使用者介面（UI）元素。

|UI 項目|描述|
|----------------|-----------------|
|**新增規則**|將新的規則定義新增至規則集。|
|**刪除**|將選取的規則從規則集內刪除。|
|**鏈結**|指定規則集要使用哪種類型的向前鏈結。 可用的選項如下：<br /><br /> -   **完整的連結**，指定使用所有的正向連結機制：隱含、方法的功能，以及使用**Update**函式的明確。<br />-   **順序**，指定不使用任何正向連結。<br />**僅 -   明確更新**，其指定只對**更新**動作執行向前連結。<br /><br /> 如需有關向前連結的詳細資訊，請參閱[使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。|
|**Name**|規則集清單資料行標題。 按一下會按照名稱排序規則清單。|
|**優先順序**|規則集清單資料行標題。 按一下會按照優先權排序規則清單。|
|**重估**|規則集清單資料行標題。 按一下會按照重新評估類型排序規則清單。|
|**規則預覽**|規則集清單資料行標題。 按一下會按照規則的條件和動作預覽排序規則清單。|
|**Name：**|輸入規則名稱。|
|**Priority：**|輸入規則的優先權。 預設優先權為 0。|
|**重估**|指定規則要使用哪一種規則重新評估。 可用的選項如下：<br /><br /> -   **一律**，這會導致規則視需要重新評估。<br />-   **never**，這會導致規則永遠不會重新評估。 在此狀況下，規則只執行一次。|
|[使用中]|核取可讓規則成為作用中。|
|**條件**|輸入規則條件的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**Then 動作：**|輸入 Then 動作的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**Else 動作：**|輸入 Else 動作的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**確定**|按一下將規則集儲存為 .rules 檔案。|

 如需規則集的詳細資訊，請參閱[使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。

## <a name="entering-condition-and-action-expressions"></a>輸入條件和動作運算式
 您可以在 [**規則集編輯器**] 對話方塊的個別文字方塊中輸入條件的運算式，以及 Then 和 Else 動作做為文字。 您可以輸入**此。** 在編輯器中，使用 IntelliSense 類型的功能表來參考工作流程中使用的欄位、屬性和方法。 或者您可以直接輸入工作流程成員名稱。 您可以輸入類別名稱，後面加上方法名稱，來呼叫參考型別上的靜態方法。

 您可以將邏輯運算子新增至條件中，如 AND、OR 和 NOT。 您也可以新增述詞 (Predicate)。 述詞是二元 (Binary) 運算子和兩個運算元。 支援的二元運算子為 = =、>、\<、> = 和 < =。 支援的運算元有常數值、算術函式和有範圍的 Public 成員。

 您可以指定比較的類型，也可以比較**null**或空字串。 您可以對包含複雜型別之變數上的成員進行巢狀呼叫，例如，`this.Address.State == "WA"`。

 運算式支援以下運算子：

- 關係運算子：==、=、!=

- 比較運算子： <、\<=、>、> =

- 算術運算子：+、-、*、/、MOD

- 邏輯運算子： AND、& &、 &#124; &#124;、、NOT、！

- 位運算子： &、&#124;

  運算式運算子的優先順序是按照 C# 運算子優先順序規則。

  如需條件的詳細資訊，請參閱[在工作流程中使用條件](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77)。

### <a name="halt-and-update-functions"></a>暫止和更新函式
 **Then 動作：** 和**Else 動作：** 運算式支援**終止**和**更新**函數。 若要使用 [**停止**] 函式，請在 [ **Then 動作：** ] 或 [**其他動作：** ] 文字方塊中輸入 [**暫停**]。 [**停止**] 動作會使規則集執行立即停止，且控制權會回到呼叫程式碼。 您可以使用**Update**函式搭配正向連結。

 **Update**語句可以在編輯器中以下列兩種形式的其中一種來表示：下列範例會顯示這兩種表單：

```
Update(this.Address.State)
Update("this/Address/State")
```

 如需有關使用**Update**搭配轉寄鏈的詳細資訊，請參閱[使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。

## <a name="see-also"></a>請參閱
 [在工作流程中](https://msdn2.microsoft.com/library/bb628447.aspx)使用[PolicyActivity 活動的](https://msdn2.microsoft.com/library/bb675229.aspx) [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [選取規則集對話方塊（舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)
