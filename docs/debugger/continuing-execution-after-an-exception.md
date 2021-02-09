---
title: 例外狀況之後繼續執行 |Microsoft Docs
description: 瞭解當偵錯工具因為未處理的例外狀況而中斷執行時，會發生什麼事。 您可以在相同的執行緒中繼續執行。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9af71aba1b26c3d8160af229d8c050038800106a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865809"
---
# <a name="continuing-execution-after-an-exception"></a>例外狀況之後繼續執行
當偵錯工具因為例外狀況而中斷執行時，預設會看到 **例外** 狀況協助程式。 如果您已在 [**選項**] 對話方塊中停用 [**例外** 狀況協助程式]，就會看到 [**例外狀況助理**] (c # 或 Visual Basic) 或 [**例外** 狀況] 對話方塊 (c + +) 。

 當 **例外** 狀況協助程式出現時，您可以嘗試修正造成例外狀況的問題。

## <a name="managed-and-native-code"></a>Managed 和機器碼
 在 managed 和機器碼中，您可以在未處理的例外狀況之後，繼續在相同的執行緒中執行。 **例外狀況 Helper** 會將呼叫堆疊回溯到擲回例外狀況的位置。

## <a name="mixed-code"></a>混合程式碼
 如果在偵錯原生和 Managed 混合的程式碼時發生未處理的例外狀況，作業系統條件約束會禁止回溯呼叫堆疊。 如果您嘗試使用捷徑功能表回溯呼叫堆疊，就會出現錯誤訊息，說明在混合程式碼偵錯期間，偵錯工具無法從未處理的例外狀況回溯。

## <a name="see-also"></a>另請參閱

- [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)