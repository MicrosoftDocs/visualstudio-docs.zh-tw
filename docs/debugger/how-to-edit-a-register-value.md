---
title: 如何： 編輯暫存器值 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 430ee5d0b36196c85d7c81b63503bfcc471d7664
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717106"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>如何： 編輯暫存器值 (C#，c + +、 Visual Basic 中， F#)

只有在透過 [選項] 對話方塊的 [偵錯] 節點啟用位址層級偵錯時，才可以使用 [暫存器] 視窗。

### <a name="to-change-the-value-of-a-register"></a>若要變更暫存器值

1.  在 [暫存器] 視窗中使用 TAB 鍵或滑鼠，將插入點移至要變更的值上。 輸入時，游標必須放在要覆寫的值的前面。

2.  輸入新值。

    > [!CAUTION]
    >  變更暫存器值 (尤其是 EIP 和 EBP 暫存器中的值) 會影響程式執行。

    > [!CAUTION]
    >  由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使表面上無害的編輯也可能造成浮點暫存器中的某些最小顯著性位元變更。

## <a name="see-also"></a>請參閱
- [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)