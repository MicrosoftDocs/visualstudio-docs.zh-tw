---
title: HOW TO：編輯暫存器值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7566d3a89ff27cc473b9352c7e0f02492dc736d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945320"
---
# <a name="how-to-edit-a-register-value"></a>HOW TO：編輯暫存器值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

只有在透過 [選項] 對話方塊的 [偵錯] 節點啟用位址層級偵錯時，才可以使用 [暫存器] 視窗。  
  
### <a name="to-change-the-value-of-a-register"></a>若要變更暫存器值  
  
1.  在 [暫存器] 視窗中使用 TAB 鍵或滑鼠，將插入點移至要變更的值上。 輸入時，游標必須放在要覆寫的值的前面。  
  
2.  輸入新值。  
  
    > [!CAUTION]
    >  變更暫存器值 (尤其是 EIP 和 EBP 暫存器中的值) 會影響程式執行。  
  
    > [!CAUTION]
    >  由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使表面上無害的編輯也可能造成浮點暫存器中的某些最小顯著性位元變更。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)
