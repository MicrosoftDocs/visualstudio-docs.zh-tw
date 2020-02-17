---
title: 逐步解說：分析瑕疵C++的 C 程式碼 |Microsoft Docs
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272444"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>逐步解說：分析 C/C++ 程式碼的缺失
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何使用 C/C++ C++ code 的程式碼分析工具，分析 c/程式碼是否有潛在的程式碼缺失。  
  
 在此逐步解說中，您將逐步執行使用程式碼分析來分析您的C++ C/程式碼是否有可能發生程式碼缺失的進程。  
  
 您將完成下列步驟：  
  
- 針對機器碼執行程式碼分析。  
  
- 分析程式碼瑕疵警告。  
  
- 將警告視為錯誤。  
  
- 標注原始程式碼以改善程式碼缺失分析。  
  
## <a name="prerequisites"></a>Prerequisites  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 或 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]。  
  
- [示範範例](../code-quality/demo-sample.md)的複本。  
  
- 對 C/C++的基本瞭解。  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>若要在機器碼上執行程式碼瑕疵分析  
  
1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟示範解決方案。  
  
     示範解決方案現在會填入**方案總管**。  
  
2. 在 [建置] 功能表上，按一下 [重建方案]。  
  
     此解決方案會建立，且不會出現任何錯誤或警告。  
  
3. 在 **方案總管**中，選取 CodeDefects 專案。  
  
4. 按一下 [專案] 功能表上的 [屬性]。  
  
     [ **CodeDefects 屬性頁**] 對話方塊隨即顯示。  
  
5. 按一下 [程式碼分析]。  
  
6. 按一下 [**啟用 C/C++ on Build 的程式碼分析**] 核取方塊。  
  
7. 重建 CodeDefects 專案。  
  
     程式碼分析警告會顯示在**錯誤清單**中。  
  
### <a name="to-analyze-code-defect-warnings"></a>若要分析程式碼瑕疵警告  
  
1. 在 [檢視] 功能表上，按一下 [錯誤清單]。  
  
     根據您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中選擇的開發人員設定檔而定，您可能必須指向 [ **View** ] 功能表上的 [**其他視窗**]，然後按一下 [**錯誤清單**]。  
  
2. 在 **錯誤清單**中，按兩下下列警告：  
  
     警告 C6230：語義不同類型之間的隱含轉換：在布林內容中使用 HRESULT。  
  
     [程式碼編輯器] 會在函式 `bool``ProcessDomain()`中顯示造成警告的那一行。 此警告表示在預期布林結果的 ' if ' 語句中使用了 HRESULT。  
  
3. 請使用 SUCCEEDED 宏來更正這個警告。 您的程式碼應該類似下列程式碼：  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. 在 **錯誤清單**中，按兩下下列警告：  
  
     警告 C6282：不正確的運算子：在測試內容中指派給常數。 Was = = 預定嗎？  
  
5. 藉由測試是否相等來更正此警告。 您的程式碼看起來應該與下列程式碼類似：  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>將警告視為錯誤  
  
1. 在錯誤 .cpp 檔案中，將下列 `#pragma` 語句加入至檔案的開頭，將警告 C6001 視為錯誤：  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. 重建 CodeDefects 專案。  
  
     在**錯誤清單**中，C6001 現在會顯示為錯誤。  
  
3. 藉由初始化 `i` 並 `j` 為0，修正**錯誤清單**中剩餘的兩個 C6001 錯誤。  
  
4. 重建 CodeDefects 專案。  
  
     專案建立時不會出現任何警告或錯誤。  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>更正 annotation 中的原始程式碼批註警告  
  
1. 在 方案總管中，選取 注釋 專案。  
  
2. 按一下 [專案] 功能表上的 [屬性]。  
  
     [**批註屬性頁**] 對話方塊隨即顯示。  
  
3. 按一下 [程式碼分析]。  
  
4. 選取 [**啟用 C/C++ on Build 的程式碼分析**] 核取方塊。  
  
5. 重建注釋專案。  
  
6. 在 **錯誤清單**中，按兩下下列警告：  
  
     警告 C6011：引用 Null 指標 ' newNode '。  
  
     此警告表示呼叫端無法檢查傳回值。 在此情況下，對**AllocateNode**的呼叫可能會傳回 Null 值（請參閱 AllocateNode 的函式聲明的注釋 .h 標頭檔）。  
  
7. 開啟注釋 .cpp 檔案。  
  
8. 若要修正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. 重建注釋專案。  
  
     專案建立時不會出現任何警告或錯誤。  
  
### <a name="to-use-source-code-annotation"></a>若要使用原始程式碼注釋  
  
1. 使用前置和後置條件（如下列範例所示），標注函數 `AddTail` 的型式參數和傳回值：  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. 重建注釋專案。  
  
3. 在 **錯誤清單**中，按兩下下列警告：  
  
     警告 C6011：引用 Null 指標 ' node '。  
  
     此警告表示傳入函式的節點可能是 null，而表示引發警告的行號。  
  
4. 若要修正這個警告，請使用 ' if ' 語句來測試傳回值。 您的程式碼應該類似下列程式碼：  
  
    ```  
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
 [逐步解說：分析 Managed 程式碼中的程式碼缺失](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
