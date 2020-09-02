---
title: 逐步解說：分析 C-C + + 缺失的程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: c822dbcc6a1ece2040da22a3442dd584c3926d97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272444"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>逐步解說：分析 C/C++ 程式碼的缺失
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說將示範如何使用 C/c + + 程式碼的程式碼分析工具，分析 C/c + + 程式碼是否有潛在的程式碼缺失。  
  
 在這個逐步解說中，您會逐步完成使用程式碼分析來分析 C/c + + 程式碼是否有潛在程式碼缺失的程式。  
  
 您將完成下列步驟：  
  
- 對原生程式碼執行程式碼分析。  
  
- 分析程式碼瑕疵的警告。  
  
- 將警告視為錯誤。  
  
- 批註原始程式碼以改善程式碼缺失分析。  
  
## <a name="prerequisites"></a>先決條件  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 或 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]。  
  
- [示範範例](../code-quality/demo-sample.md)的複本。  
  
- C/c + + 的基本瞭解。  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>若要執行機器碼的程式碼瑕疵分析  
  
1. 開啟中的示範方案 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
     示範解決方案現在會填入 **方案總管**。  
  
2. 在 [建置]**** 功能表上，按一下 [重建方案]****。  
  
     解決方案會建立，而不會發生任何錯誤或警告。  
  
3. 在 **方案總管**中，選取 CodeDefects 專案。  
  
4. 按一下 [專案] 功能表上的 [屬性]。  
  
     [ **CodeDefects 屬性頁** ] 對話方塊隨即顯示。  
  
5. 按一下 [程式碼分析]。  
  
6. 按一下 [ **在組建上啟用 c/c + + 的程式碼分析** ] 核取方塊。  
  
7. 重建 CodeDefects 專案。  
  
     程式碼分析警告會顯示在 [ **錯誤清單**] 中。  
  
### <a name="to-analyze-code-defect-warnings"></a>若要分析程式碼缺失警告  
  
1. 在 [檢視] 功能表上，按一下 [錯誤清單]。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後按一下 [**錯誤清單**]，視您在中選擇的開發人員設定檔而定。  
  
2. 在 [ **錯誤清單**] 中，按兩下下列警告：  
  
     警告 C6230：語義不同類型之間的隱含轉換：在布林內容中使用 HRESULT。  
  
     程式碼編輯器會顯示在函式中造成警告的行 `bool``ProcessDomain()` 。 此警告表示在預期布林結果的 ' if ' 語句中使用 HRESULT。  
  
3. 使用 SUCCEEDED 宏來修正這個警告。 您的程式碼應該類似下列程式碼：  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. 在 [ **錯誤清單**] 中，按兩下下列警告：  
  
     警告 C6282：不正確的運算子：指派給測試內容中的常數。 Was = = 預期嗎？  
  
5. 測試是否相等以修正這個警告。 您的程式碼看起來應該類似下列程式碼：  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>將警告視為錯誤  
  
1. 在 Bug .cpp 檔案中，將下列語句加入 `#pragma` 至檔案的開頭，以將警告 C6001 視為錯誤：  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. 重建 CodeDefects 專案。  
  
     在 [ **錯誤清單**] 中，C6001 現在會顯示為錯誤。  
  
3. 藉由初始化和至0，修正 **錯誤清單** 中剩餘的兩個 C6001 錯誤 `i` `j` 。  
  
4. 重建 CodeDefects 專案。  
  
     專案建立時不會出現任何警告或錯誤。  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>更正 annotation 中的原始程式碼批註警告  
  
1. 在方案總管中，選取 [注釋] 專案。  
  
2. 按一下 [專案] 功能表上的 [屬性]。  
  
     [ **批註屬性頁** ] 對話方塊隨即顯示。  
  
3. 按一下 [程式碼分析]。  
  
4. 選取 [ **在組建上啟用 c/c + + 的程式碼分析** ] 核取方塊。  
  
5. 重建批註專案。  
  
6. 在 [ **錯誤清單**] 中，按兩下下列警告：  
  
     警告 C6011：對 Null 指標 ' newNode ' 取值。  
  
     此警告表示呼叫端檢查傳回值失敗。 在此情況下，對 **AllocateNode** 的呼叫可能會傳回 Null 值 (請參閱 AllocateNode) 函式宣告的注釋 .h 標頭檔。  
  
7. 開啟批註 .cpp 檔案。  
  
8. 若要更正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. 重建批註專案。  
  
     專案建立時不會出現任何警告或錯誤。  
  
### <a name="to-use-source-code-annotation"></a>使用原始程式碼注釋  
  
1. 使用前置和後置條件來標注函式的正式參數和傳回值， `AddTail` 如下列範例所示：  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. 重建批註專案。  
  
3. 在 [ **錯誤清單**] 中，按兩下下列警告：  
  
     警告 C6011：參考 Null 指標 ' node '。  
  
     此警告表示傳遞至函式的節點可能為 null，並指出引發警告的行號。  
  
4. 若要更正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. 重建批註專案。  
  
     專案建立時不會出現任何警告或錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：分析 Managed 程式碼中的程式碼缺失](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
