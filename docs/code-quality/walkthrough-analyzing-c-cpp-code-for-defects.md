---
title: 逐步解說：分析 C/C++ 程式碼的缺失
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: bdb99cf487995859b9623f11b3559f1b5e7e3ca7
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018349"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>逐步解說：分析 C/C++ 程式碼的缺失

本逐步解說示範如何使用 C/C++ C++ code 的程式碼分析工具，分析 c/程式碼是否有潛在的程式碼缺失。

- 針對機器碼執行程式碼分析。
- 分析程式碼瑕疵警告。
- 將警告視為錯誤。
- 標注原始程式碼以改善程式碼缺失分析。

## <a name="prerequisites"></a>必要條件

- [示範範例](../code-quality/demo-sample.md)的複本。
- 對 C/C++的基本瞭解。

### <a name="to-run-code-defect-analysis-on-native-code"></a>若要在機器碼上執行程式碼瑕疵分析

1. 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟示範解決方案。

     示範解決方案現在會填入**方案總管**。

2. 在 [建置] 功能表上，按一下 [重建方案]。

     此解決方案會建立，且不會出現任何錯誤或警告。

3. 在 **方案總管**中，選取 CodeDefects 專案。

4. 在 [專案] 功能表上，按一下 [屬性]。

     [ **CodeDefects 屬性頁**] 對話方塊隨即顯示。

5. 按一下 [程式**代碼分析**]。

6. 按一下 [**啟用 C/C++ on Build 的程式碼分析**] 核取方塊。

7. 重建 CodeDefects 專案。

     程式碼分析警告會顯示在**錯誤清單**中。

### <a name="to-analyze-code-defect-warnings"></a>若要分析程式碼瑕疵警告

1. 在 [ **View** ] 功能表上，按一下 [**錯誤清單**]。

     根據您在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中選擇的開發人員設定檔而定，您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後按一下 [**錯誤清單**]。

2. 在 **錯誤清單**中，按兩下下列警告：

     警告 C6230：語義不同類型之間的隱含轉換：在布林內容中使用 HRESULT。

     [程式碼編輯器] 會在函數中顯示導致警告的那一行 `bool ProcessDomain()`。 此警告表示在預期布林結果的 ' if ' 語句中使用了 HRESULT。

3. 請使用 SUCCEEDED 宏來更正這個警告。 您的程式碼應該類似下列程式碼：

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. 在 **錯誤清單**中，按兩下下列警告：

     警告 C6282：不正確的運算子：在測試內容中指派給常數。 Was = = 預定嗎？

5. 藉由測試是否相等來更正此警告。 您的程式碼看起來應該與下列程式碼類似：

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>將警告視為錯誤

1. 在 Bug .cpp 檔案中，將下列 `#pragma` 語句加入至檔案的開頭，將警告 C6001 視為錯誤：

   ```cpp
   #pragma warning (error: 6001)
   ```

2. 重建 CodeDefects 專案。

     在**錯誤清單**中，C6001 現在會顯示為錯誤。

3. 藉由初始化 `i` 並 `j` 為0，來更正**錯誤清單**中剩餘的兩個 C6001 錯誤。

4. 重建 CodeDefects 專案。

     專案建立時不會出現任何警告或錯誤。

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>更正 annotation 中的原始程式碼批註警告

1. 在 方案總管中，選取 注釋 專案。

2. 在 [專案] 功能表上，按一下 [屬性]。

     [**批註屬性頁**] 對話方塊隨即顯示。

3. 按一下 [程式**代碼分析**]。

4. 選取 [**啟用 C/C++ on Build 的程式碼分析**] 核取方塊。

5. 重建注釋專案。

6. 在 **錯誤清單**中，按兩下下列警告：

     警告 C6011：引用 Null 指標 ' newNode '。

     此警告表示呼叫端無法檢查傳回值。 在此情況下，對**AllocateNode**的呼叫可能會傳回 Null 值（請參閱 AllocateNode 的函式聲明的注釋 .h 標頭檔）。

7. 開啟注釋 .cpp 檔案。

8. 若要修正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. 重建注釋專案。

     專案建立時不會出現任何警告或錯誤。

### <a name="to-use-source-code-annotation"></a>若要使用原始程式碼注釋

1. 使用前置和後置條件（如下列範例所示），標注函式的正式參數和傳回值 `AddTail`：

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. 重建注釋專案。

3. 在 **錯誤清單**中，按兩下下列警告：

     警告 C6011：引用 Null 指標 ' node '。

     此警告表示傳入函式的節點可能是 null，而表示引發警告的行號。

4. 若要修正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. 重建注釋專案。

     專案建立時不會出現任何警告或錯誤。

## <a name="see-also"></a>另請參閱

[逐步解說：分析 Managed 程式碼的程式碼缺失 @ no__t-0 @ no__t-1 程式[代碼分析C++ （適用于 C/](../code-quality/code-analysis-for-c-cpp-overview.md) ）
