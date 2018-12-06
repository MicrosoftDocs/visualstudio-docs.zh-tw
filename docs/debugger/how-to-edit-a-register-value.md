---
title: 如何： 編輯暫存器值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0337f7c77d1ed601c7a6c13c702f4758cbfdbd
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257068"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>如何： 編輯暫存器值 (C#，c + +、 Visual Basic 中， F#)

暫存器視窗是在已啟用位址層級偵錯時，才可以使用**選項** 對話方塊中，**偵錯**節點。  
  
### <a name="to-change-the-value-of-a-register"></a>若要變更暫存器值  
  
1.  在 **註冊**視窗中，使用 TAB 鍵或滑鼠來移動插入點到您想要變更的值。 輸入時，游標必須放在要覆寫的值的前面。  
  
2.  輸入新值。  
  
    > [!CAUTION]
    >  變更暫存器值 (尤其是 EIP 和 EBP 暫存器中的值) 會影響程式執行。  
  
    > [!CAUTION]
    >  由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使表面上無害的編輯也可能造成浮點暫存器中的某些最小顯著性位元變更。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)