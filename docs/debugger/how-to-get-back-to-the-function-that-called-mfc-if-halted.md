---
title: 回到呼叫 MFC，如果暫止的函式 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c746fc287435ea6219e0f6052bc9372fc2ae5d25
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048564"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>HOW TO：於暫止時回到呼叫 MFC 的函式

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

如果您使用 [偵錯] 功能表上的 [中斷] 命令來暫止程式並於 MFC 中結束，而且您確定問題位於程式碼時，可以使用 [呼叫堆疊] 視窗巡覽回該函式。 如需詳細資訊，請參閱[＜How to：使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md)。

有時候，您的程式碼可能會在訊息幫浦內中斷。 如果發生這種情形，呼叫堆疊上不會有任何使用者程式碼。 若要避免發生此問題，您可以改用中斷點 (可能含條件與叫用次數) 來取代 [中斷] 命令。 如需詳細資訊，請參閱 [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)。

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>瀏覽至呼叫 MFC 的函式

-   使用 [呼叫堆疊] 視窗。

## <a name="see-also"></a>另請參閱

- [偵錯機器碼常見問題集](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)