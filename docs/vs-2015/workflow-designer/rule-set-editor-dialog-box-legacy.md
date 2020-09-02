---
title: " (舊版) 的 [規則集編輯器] 對話方塊 |Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846319"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>規則集編輯器對話方塊 (舊版)
本主題描述如何在舊版中使用 [ **規則集編輯器** ] 對話方塊 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

 [ **規則集編輯器** ] 對話方塊是用來建立和修改 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) 規則集，這些規則集會序列化為 rules 檔。

> [!NOTE]
> 如果您想要使用 **XML 編輯器搭配編碼**來開啟此檔案，您必須先關閉工作流程或活動的相關設計工具視窗。

 如需如何存取 [ **規則集編輯器** ] 對話方塊的詳細資訊，請參閱 [如何：建立 PolicyActivity 規則集 (舊版) ](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)。

> [!WARNING]
> 舊版 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 的規則編輯器，它所針對的 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 或 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 不支援多重目標。

 下表說明 [ **規則集編輯器** ] 對話方塊中， (UI) 專案的使用者介面。

|UI 元素|說明|
|----------------|-----------------|
|**新增規則**|將新的規則定義新增至規則集。|
|**刪除**|將選取的規則從規則集內刪除。|
|**鏈結**|指定規則集要使用哪種類型的向前鏈結。 可用的選項如下：<br /><br /> -   **完整連結**：指定要使用所有正向連結機制：隱含、方法的特性化，以及使用 **Update** 函數的明確。<br />-   **順序**，指定不使用任何轉寄鏈。<br />-   **僅限明確更新**，指定只執行 **更新** 動作的向前連結。<br /><br /> 如需有關向前連結的詳細資訊，請參閱 [使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。|
|**名稱**|規則集清單資料行標題。 按一下會按照名稱排序規則清單。|
|**優先順序**|規則集清單資料行標題。 按一下會按照優先權排序規則清單。|
|**重新評估**|規則集清單資料行標題。 按一下會按照重新評估類型排序規則清單。|
|**規則預覽**|規則集清單資料行標題。 按一下會按照規則的條件和動作預覽排序規則清單。|
|**名稱:**|輸入規則名稱。|
|**優先：**|輸入規則的優先權。 預設優先權為 0。|
|**再：**|指定規則要使用哪一種規則重新評估。 可用的選項如下：<br /><br /> -   **永遠**，這會視需要重新評估規則。<br />-   **絕對**不會重新評估規則。 在此狀況下，規則只執行一次。|
|**使用中**|核取可讓規則成為作用中。|
|**條件：**|輸入規則條件的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**Then 動作:**|輸入 Then 動作的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**Else 動作:**|輸入 Else 動作的運算式。 如需運算式語法的詳細資訊，請參閱本頁的「輸入條件和動作運算式」一節。|
|**確定**|按一下將規則集儲存為 .rules 檔案。|

 如需規則集的詳細資訊，請參閱 [使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。

## <a name="entering-condition-and-action-expressions"></a>輸入條件和動作運算式
 您可以在 [ **規則集編輯器** ] 對話方塊的個別文字方塊中，輸入條件的運算式和 [Then] 和 [Else] 動作做為文字。 您可以輸入 **這個。** 在編輯器中，使用 IntelliSense 類型的功能表，來參考工作流程中使用的欄位、屬性和方法。 或者您可以直接輸入工作流程成員名稱。 您可以輸入類別名稱，後面加上方法名稱，來呼叫參考型別上的靜態方法。

 您可以將邏輯運算子新增至條件中，如 AND、OR 和 NOT。 您也可以加入述詞。 述詞是二元 (Binary) 運算子和兩個運算元。 支援的二元運算子為 = =、>、 \<, > = 和 <=。 支援的運算元有常數值、算術函式和有範圍的 Public 成員。

 您可以指定比較的型別，也可以比較 **null** 或空字串。 您可以對包含複雜型別之變數上的成員進行巢狀呼叫，例如，`this.Address.State == "WA"`。

 運算式支援以下運算子：

- 關係運算子：==、=、!=

- 比較運算子： <、 \<=, > 、>=

- 算術運算子：+、-、*、/、MOD

- 邏輯運算子： AND、 &&、OR、 &#124;&#124;、NOT、！

- 位運算子： &、&#124;

  運算式運算子的優先順序是按照 C# 運算子優先順序規則。

  如需條件的詳細資訊，請參閱 [在工作流程中使用條件](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77)。

### <a name="halt-and-update-functions"></a>暫止和更新函式
 **Then 動作：** 和 **Else 動作：** 運算式支援 **終止** 和 **更新** 函數。 若要使用**暫停**函式，請在 [ **Then 動作：** ] 或 [ **Else 動作：** ] 文字方塊中輸入**暫停**。 **停止**動作會導致規則集執行立即停止，並將控制權返回呼叫程式碼。 您可以搭配使用 **Update** 函數與正向連結。

 您可以使用下列兩種格式之一，在編輯器中表示 **Update** 語句。下列範例會顯示這兩種表單：

```
Update(this.Address.State)
Update("this/Address/State")
```

 如需有關使用 **Update** 搭配向前連結的詳細資訊，請參閱 [使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。

## <a name="see-also"></a>另請參閱
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [選取規則集對話方塊 (舊版) ](../workflow-designer/select-rule-set-dialog-box-legacy.md)使用[工作流程中的條件](https://msdn2.microsoft.com/library/bb628447.aspx)[來使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)
