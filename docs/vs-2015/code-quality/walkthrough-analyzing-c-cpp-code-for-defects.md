---
title: 逐步解說： 分析 C-C + + 程式碼的缺失 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f5c2f6bfeabb80c03b1940ada2f57abbefb60173
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272638"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>逐步解說：分析 C/C++ 程式碼的缺失
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何使用 C/c + + 程式碼的程式碼分析工具分析 C/c + + 程式碼有潛在的程式碼缺失。  
  
 在本逐步解說中，您逐步完成程序使用程式碼分析來分析您的 C/c + + 程式碼有潛在的程式碼缺失。  
  
 您將完成下列步驟：  
  
-   執行程式碼分析原生程式碼。  
  
-   分析程式碼缺失警告。  
  
-   將警告視為錯誤。  
  
-   加上註解來改善程式碼缺失分析的來源程式碼。  
  
## <a name="prerequisites"></a>必要條件  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 或 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]。  
  
-   一份[示範範例](../code-quality/demo-sample.md)。  
  
-   基本的 C/c + + 的了解。  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>在原生程式碼執行的程式碼缺失分析  
  
1.  示範中開啟方案[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
     示範解決方案現在會填入**方案總管 中**。  
  
2.  在 **建置**功能表上，按一下**重建方案**。  
  
     沒有任何錯誤或警告，建置方案。  
  
3.  在 **方案總管 中**，選取 CodeDefects 專案。  
  
4.  在 [專案] 功能表上，按一下 [屬性]。  
  
     **CodeDefects 屬性頁**對話方塊隨即出現。  
  
5.  按一下 **程式碼分析**。  
  
6.  按一下 **啟用 C/c + + 建置的程式碼分析**核取方塊。  
  
7.  重建 CodeDefects 專案。  
  
     程式碼分析警告會顯示在**錯誤清單**。  
  
### <a name="to-analyze-code-defect-warnings"></a>若要分析的程式碼缺失警告  
  
1.  在 **檢視**功能表上，按一下**錯誤清單**。  
  
     根據您在所選擇的開發人員設定檔[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，您可能必須指向**其他 Windows**上**檢視**功能表，然後再按一下**錯誤清單**。  
  
2.  在 **錯誤清單**，連按兩下 下列警告：  
  
     警告 C6230： 語意不相同的類型之間發生不當隱含轉換： 在布林內容中使用 HRESULT。  
  
     程式碼編輯器中顯示的函式中造成警告的行`bool``ProcessDomain()`。 這則警告表示 HRESULT 正在使用 'if' 陳述式中所預期布林結果的位置。  
  
3.  使用 SUCCEEDED 巨集，以更正這個警告。 您的程式碼看起來應該像下列程式碼：  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  在 **錯誤清單**，連按兩下 下列警告：  
  
     警告 C6282： 不正確的運算子： 測試內容中的指派常數。 是 = = 預期？  
  
5.  測試相等，以更正這個警告。 您的程式碼看起來應該類似下列的程式碼：  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>若要將警告視為錯誤  
  
1.  在 Bug.cpp 檔案中，新增下列`#pragma`要視為錯誤的警告 C6001 檔案開頭的陳述式：  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  重建 CodeDefects 專案。  
  
     在 **錯誤清單**，C6001 現在會顯示為錯誤。  
  
3.  修正中其餘的兩個 C6001 錯誤**錯誤清單**初始化`i`和`j`設為 0。  
  
4.  重建 CodeDefects 專案。  
  
     專案組建，而不出現任何警告或錯誤。  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>若要更正來源的程式碼註解中的警告，annotation.c  
  
1.  在 方案總管 中，選取 註解專案。  
  
2.  在 [專案] 功能表上，按一下 [屬性]。  
  
     **附註屬性頁**對話方塊隨即出現。  
  
3.  按一下 **程式碼分析**。  
  
4.  選取 **啟用 C/c + + 建置的程式碼分析**核取方塊。  
  
5.  重建註解的專案。  
  
6.  在 **錯誤清單**，連按兩下 下列警告：  
  
     警告 C6011： 取值 NULL 指標 'newNode'。  
  
     這則警告表示由呼叫端無法檢查傳回的值。 在此情況下，呼叫**AllocateNode**可能會傳回 NULL 值 （請參閱 AllocateNode 的函式宣告的 annotations.h 標頭檔）。  
  
7.  開啟 annotations.cpp 檔案。  
  
8.  若要更正這個警告，請使用 'if' 陳述式，測試傳回的值。 您的程式碼看起來應該像下列程式碼：  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. 重建註解的專案。  
  
     專案組建，而不出現任何警告或錯誤。  
  
### <a name="to-use-source-code-annotation"></a>若要使用來源的程式碼註解  
  
1.  標註型式參數和傳回值的函式`AddTail`所使用的前置和後置條件，在此範例中所示：  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  重建註解的專案。  
  
3.  在 **錯誤清單**，連按兩下 下列警告：  
  
     警告 C6011： 取值 NULL 指標 'node'。  
  
     這則警告指出傳遞至函式的節點可能為 null，並指出發生警告的行號。  
  
4.  若要更正這個警告，請使用 'if' 陳述式，測試傳回的值。 您的程式碼看起來應該像下列程式碼：  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  重建註解的專案。  
  
     專案組建，而不出現任何警告或錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：分析 Managed 程式碼中的程式碼缺失](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)



