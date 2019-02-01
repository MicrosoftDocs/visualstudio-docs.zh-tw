---
title: 在編輯後繼續的中斷模式套用編輯 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1f43582b9511aa8effda93a083b6117c42a9a57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925472"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>HOW TO：套用在中斷模式中的編輯，以編輯後繼續 (Visual Basic)
您可以在中斷模式中使用 [編輯後繼續] 編輯程式碼，並繼續進行而不需停止及重新啟動執行。  
  
如需有關使用 編輯後繼續偵錯時的限制，請參閱[支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)。
  
### <a name="to-edit-code-in-break-mode"></a>在中斷模式中編輯程式碼  
  
1.  執行下列其中一種方法進入中斷模式  
  
    -   在程式碼中設定中斷點，然後從 [偵錯] 功能表中選擇 [開始偵錯]，並等待應用程式叫用中斷點。  
  
         -或-  
  
    -   開始偵錯，然後從 [偵錯] 功能表中選取 [全部中斷]。  
  
         -或-  
  
    -   發生例外狀況時，選擇**啟用編輯**上**例外狀況助理**。  
  
2.  進行任何所需和所支援的程式碼變更。  
  
     如需詳細資訊，請參閱 <<c0> [ 支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)。</c0>  
  
    > [!NOTE]
    >  如果您嘗試進行 [編輯後繼續] 不允許的程式碼變更，您的編輯會被加上紫色波浪線，而且 [工作清單] 中會出現工作。 除非您復原不合法的程式碼變更，否則將無法繼續執行程式碼。  
  
3.  在 [偵錯] 功能表上，按一下 [繼續] 以恢復執行。  
  
     這時程式碼便會一併執行您套用至專案的編輯。  
  
## <a name="see-also"></a>請參閱  
 [支援的程式碼變更 (C#和 Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 [編輯後繼續 (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
