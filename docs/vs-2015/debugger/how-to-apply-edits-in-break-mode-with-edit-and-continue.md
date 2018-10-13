---
title: 如何： 套用在中斷模式中的編輯，以編輯後繼續 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ebab549e6d32b355355e4970f4191ea9a024e871
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266379"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>如何：以編輯後繼續在中斷模式套用編輯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在中斷模式中使用 [編輯後繼續] 編輯程式碼，並繼續進行而不需停止及重新啟動執行。  
  
 [編輯後繼續] 無法用於下列偵錯案例中：  
  
-   混合模式 (原生/Managed) 偵錯。  
  
-   SQL 偵錯  
  
-   偵錯 Dr.Watson 傾印。  
  
-   在未選取 [ **發生未處理的例外狀況時回溯呼叫堆疊** ] 選項的情況下，於發生未處理的例外狀況後編輯程式碼。  
  
-   偵錯內嵌的執行階段應用程式。  
  
-   偵錯的應用程式**附加至**而不是執行應用程式**開始**從**偵錯**功能表。  
  
-   偵錯最佳化程式碼  
  
-   當目標為 64 位元應用程式時，偵錯 Managed 程式碼。 如果要使用 [編輯後繼續]，就必須將目標設定為 x86  (_專案_**屬性**，**編譯**索引標籤上，**進階編譯器**設定。)。  
  
-   由於建置錯誤以致新版本建置失敗之後，請偵錯舊版的程式碼。  
  
### <a name="to-edit-code-in-break-mode"></a>在中斷模式中編輯程式碼  
  
1.  執行下列其中一種方法進入中斷模式  
  
    -   您的程式碼中設定中斷點，然後選擇**開始偵錯**從**偵錯**功能表，然後等待應用程式叫用中斷點。  
  
         -或-  
  
    -   開始偵錯，然後按**全部中斷**從**偵錯**功能表。  
  
         -或-  
  
    -   發生例外狀況時，選擇**啟用編輯**上**例外狀況助理**。  
  
2.  進行想要並正確的程式碼變更。  
  
     如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 編輯後繼續中不支援編輯](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)。  
  
    > [!NOTE]
    >  如果您嘗試進行 [編輯後繼續] 不允許的程式碼變更，您的編輯會被加上紫色波浪線，而且 [工作清單] 中會出現工作。 除非您復原不合法的程式碼變更，否則將無法繼續執行程式碼。  
  
3.  在 [**偵錯**] 功能表中，按一下**繼續**恢復執行。  
  
     這時程式碼便會一併執行您套用至專案的編輯。  
  
## <a name="see-also"></a>另請參閱  
 [編輯後繼續在 Visual Basic 中的不支援的編輯](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [編輯後繼續 (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



