---
title: 逐步解說：分析 C/C++ 程式碼的缺失
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 60cdc07b35480509152fd09fefb484557358fba0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>逐步解說：分析 C/C++ 程式碼的缺失

本逐步解說示範如何使用 C/c + + 程式碼的程式碼分析工具分析 C/c + + 程式碼有潛在的程式碼缺失。

- 執行原生程式碼的程式碼分析。
- 分析程式碼缺失警告。
- 將警告視為錯誤。
- 原始程式碼，以改善程式碼缺失分析加上註解。

## <a name="prerequisites"></a>必要條件

- 一份[示範範例](../code-quality/demo-sample.md)。
- C/c + + 的基本了解。

### <a name="to-run-code-defect-analysis-on-native-code"></a>在原生程式碼執行程式碼缺失分析

1. 示範中開啟方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

     Demo 方案隨即填入**方案總管 中**。

2. 在**建置**功能表上，按一下 **重建方案**。

     沒有任何錯誤或警告，建置方案。

3. 在**方案總管 中**，選取 CodeDefects 專案。

4. 在 [專案] 功能表上，按一下 [屬性]。

     **CodeDefects 屬性頁**對話方塊隨即出現。

5. 按一下**程式碼分析**。

6. 按一下**啟用 C/c + + 建置的程式碼分析**核取方塊。

7. 重建 CodeDefects 專案。

     程式碼分析警告會顯示在**錯誤清單**。

### <a name="to-analyze-code-defect-warnings"></a>若要分析的程式碼缺失警告

1. 在**檢視**功能表上，按一下 **錯誤清單**。

     根據您在所選擇的開發人員設定檔[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，您可能必須指向**其他視窗**上**檢視**功能表，然後再按一下**錯誤清單**。

2. 在**錯誤清單**，按兩下下列警告：

     警告 C6230： 語意不相同的類型之間發生不當隱含轉型： 在布林內容中使用 HRESULT。

     程式碼編輯器會顯示函式中造成警告的行， `bool``ProcessDomain()`。 這個警告表示 HRESULT 正在使用 'if' 陳述式中卻布林結果。

3. 使用 SUCCEEDED 巨集，以更正這個警告。 您的程式碼應該類似下列程式碼：

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. 在**錯誤清單**，按兩下下列警告：

     警告 C6282： 不正確的運算子： 指派給測試內容中的常數。 是 = = 預期？

5. 更正這個警告，藉由測試相等。 您的程式碼看起來應該類似下列程式碼：

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>若要將警告視為錯誤

1. 在 Bug.cpp 檔案中，加入下列`#pragma`要視為錯誤的警告 C6001 檔案開頭的陳述式：

   ```cpp
   #pragma warning (error: 6001)
   ```

2. 重建 CodeDefects 專案。

     在**錯誤清單**，C6001 現在會顯示為錯誤。

3. 更正中其餘的兩個 C6001 錯誤**錯誤清單**初始化`i`和`j`設為 0。

4. 重建 CodeDefects 專案。

     專案建置時沒有任何警告或錯誤訊息。

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>若要更正來源的程式碼註解中的警告，annotation.c

1. 在 [方案總管] 中選取的註解專案。

2. 在 [專案] 功能表上，按一下 [屬性]。

     **附註屬性頁**對話方塊隨即出現。

3. 按一下**程式碼分析**。

4. 選取**啟用 C/c + + 建置的程式碼分析**核取方塊。

5. 重建專案註解。

6. 在**錯誤清單**，按兩下下列警告：

     警告 C6011： 取值 NULL 指標 'newNode'。

     這個警告表示失敗的呼叫端要檢查的傳回值。 在這個情況下，呼叫**AllocateNode**可能會傳回 NULL 值 （請參閱 AllocateNode 函式宣告的 annotations.h 標頭檔）。

7. 開啟 annotations.cpp 檔案。

8. 若要修正這個警告，使用的 'if' 陳述式測試傳回的值。 您的程式碼應該類似下列程式碼：

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. 重建專案註解。

     專案建置時沒有任何警告或錯誤訊息。

### <a name="to-use-source-code-annotation"></a>若要使用來源的程式碼註解

1. 標註型式參數和傳回值的函式`AddTail`使用前置和後置條件，在此範例所示：

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. 重建註釋的專案。

3. 在**錯誤清單**，按兩下下列警告：

     警告 C6011： 取值 NULL 指標 'node'。

     這個警告指出，傳遞至函式的節點可能是 null，而且表示引發警告的行號。

4. 若要修正這個警告，使用的 'if' 陳述式測試傳回的值。 您的程式碼應該類似下列程式碼：

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. 重建註釋的專案。

     專案建置時沒有任何警告或錯誤訊息。

## <a name="see-also"></a>另請參閱

[逐步解說： 分析 Managed 程式碼的程式碼缺失](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[C/c + + 程式碼分析](../code-quality/code-analysis-for-c-cpp-overview.md)