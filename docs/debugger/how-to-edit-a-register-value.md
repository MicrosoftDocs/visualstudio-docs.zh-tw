---
title: "如何： 編輯暫存器值 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b9cc839b7829070f5d4c2e9db9da12b6522c21eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-a-register-value"></a>如何：編輯暫存器值
暫存器視窗是在已啟用位址層級偵錯時，才可以使用**選項**對話方塊中，**偵錯**節點。  
  
### <a name="to-change-the-value-of-a-register"></a>若要變更暫存器值  
  
1.  在**註冊**視窗中，使用 TAB 鍵或滑鼠來移動插入點到您想要變更的值。 輸入時，游標必須放在要覆寫的值的前面。  
  
2.  輸入新值。  
  
    > [!CAUTION]
    >  變更暫存器值 (尤其是 EIP 和 EBP 暫存器中的值) 會影響程式執行。  
  
    > [!CAUTION]
    >  由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使表面上無害的編輯也可能造成浮點暫存器中的某些最小顯著性位元變更。  
  
## <a name="see-also"></a>請參閱  
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)