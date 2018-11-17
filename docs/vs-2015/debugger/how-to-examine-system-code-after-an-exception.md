---
title: 如何： 在例外狀況後檢查系統程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cbaff38cdd6d769140f135d319a88d6098f294b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729040"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>如何：在發生例外狀況後檢查系統程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

發生例外狀況 (Exception) 時，您可能必須檢查系統呼叫內部的程式碼，判斷造成例外狀況的原因。 下列程序說明如果您沒有載入系統程式碼的符號，或是在已經啟用 Just My Code 的情況下，如何執行這項工作。  
  
### <a name="to-examine-system-code-following-an-exception"></a>若要在發生例外狀況後檢查系統程式碼  
  
1.  在 [**呼叫堆疊**] 視窗中，按一下滑鼠右鍵，然後按一下**顯示外部程式碼**。  
  
     如果未啟用 Just My Code，捷徑功能表上就不會提供這個選項，而且預設會顯示系統程式碼。  
  
2.  以滑鼠右鍵按一下現在出現在外部程式碼框架**呼叫堆疊**視窗。  
  
3.  指向**載入符號來源**，然後按一下**Microsoft 符號伺服器**。  
  
    1.  如果 Just My Code 已啟用，將會出現一個對話方塊， 指出 Just My Code 現在已經停用。 這是逐步執行系統呼叫的必要動作。  
  
    2.  **正在下載公用符號** 對話方塊隨即出現。 下載完成後，這個對話方塊就會消失。  
  
4.  您現在可以檢查系統程式碼中的**呼叫堆疊**視窗和其他視窗。 例如，您可以按兩下檢視程式碼，在來源中的呼叫堆疊框架或**反組譯碼**視窗。  
  
## <a name="see-also"></a>另請參閱  
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)





