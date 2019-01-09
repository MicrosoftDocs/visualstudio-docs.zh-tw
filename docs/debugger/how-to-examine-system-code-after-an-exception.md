---
title: 在 例外狀況後檢查系統程式碼 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ea7f4223a6d61faa852d7985f77f4f672d26d17
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878636"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>HOW TO：在發生例外狀況後檢查系統程式碼
發生例外狀況 (Exception) 時，您可能必須檢查系統呼叫內部的程式碼，判斷造成例外狀況的原因。 下列程序說明如果您沒有載入系統程式碼的符號，或是在已經啟用 Just My Code 的情況下，如何執行這項工作。  
  
### <a name="to-examine-system-code-following-an-exception"></a>若要在發生例外狀況後檢查系統程式碼  
  
1.  在 [呼叫堆疊] 視窗中按一下滑鼠右鍵，然後按一下 [顯示外部程式碼]。  
  
     如果未啟用 Just My Code，捷徑功能表上就不會提供這個選項，而且預設會顯示系統程式碼。  
  
2.  以滑鼠右鍵按一下現在出現在 [呼叫堆疊] 視窗中的外部程式碼框架。  
  
3.  指向 [載入符號來源]，然後按一下 [Microsoft 符號伺服器]。  
  
    1.  如果 Just My Code 已啟用，將會出現一個對話方塊， 指出 Just My Code 現在已經停用。 這是逐步執行系統呼叫的必要動作。  
  
    2.  [正在下載公用符號] 對話方塊隨即出現。 下載完成後，這個對話方塊就會消失。  
  
4.  您現在可以在 [呼叫堆疊] 視窗和其他視窗中檢查系統程式碼。 例如，您可以按兩下呼叫框架，在來源或 [反組譯碼] 視窗中檢視程式碼。  
  
## <a name="see-also"></a>請參閱  
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)