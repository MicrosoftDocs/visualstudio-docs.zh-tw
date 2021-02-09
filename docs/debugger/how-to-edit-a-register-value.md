---
title: 編輯暫存器值 |Microsoft Docs
description: 瞭解如何藉由在 [暫存器] 視窗中編輯其值來修改暫存器的內容， (只有在已啟用) 的位址層級偵錯工具才能使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4187be3bd4d5d2099374acea58d86bd093538ef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917374"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>如何：編輯暫存器值 (c #、c + +、Visual Basic、F # ) 

只有在透過 [選項] 對話方塊的 [偵錯] 節點啟用位址層級偵錯時，才可以使用 [暫存器] 視窗。

### <a name="to-change-the-value-of-a-register"></a>若要變更暫存器值

1. 在 [暫存器] 視窗中使用 TAB 鍵或滑鼠，將插入點移至要變更的值上。 輸入時，游標必須放在要覆寫的值的前面。

2. 輸入新值。

    > [!CAUTION]
    > 變更暫存器值 (尤其是 EIP 和 EBP 暫存器中的值) 會影響程式執行。

    > [!CAUTION]
    > 由於分數元件的十進位至二進位轉換，編輯浮點數值會略微不精確。 即使表面上無害的編輯也可能造成浮點暫存器中的某些最小顯著性位元變更。

## <a name="see-also"></a>另請參閱
- [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)