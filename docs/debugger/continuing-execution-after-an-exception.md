---
title: 例外狀況之後繼續執行 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d557fc0ec056cac22603338f95920e5c721f67dd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637278"
---
# <a name="continuing-execution-after-an-exception"></a>例外狀況之後繼續執行
當偵錯工具中斷執行，因為發生例外狀況時，您會看到**例外狀況協助程式**，根據預設。 如果您已停用**例外狀況協助程式**中**選項** 對話方塊中，您會看到**例外狀況助理**(C#或 Visual Basic) 或**例外狀況**對話方塊 （c + +）。

 當**例外狀況協助程式**出現時，您可以嘗試修正造成例外狀況的問題。

## <a name="managed-and-native-code"></a>Managed 和原生程式碼
 在 managed 和原生程式碼中，您可以在相同的執行緒繼續執行之後處理的例外狀況。 **例外狀況協助程式**回溯呼叫堆疊來擲回例外狀況的位置。

## <a name="mixed-code"></a>混合程式碼
 如果在偵錯原生和 Managed 混合的程式碼時發生未處理的例外狀況，作業系統條件約束會禁止回溯呼叫堆疊。 如果您嘗試使用捷徑功能表回溯呼叫堆疊，就會出現錯誤訊息，說明在混合程式碼偵錯期間，偵錯工具無法從未處理的例外狀況回溯。

## <a name="see-also"></a>請參閱

- [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)