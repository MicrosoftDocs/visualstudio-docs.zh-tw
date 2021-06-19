---
title: 回到呼叫 MFC 的函式（如果已暫停） |Microsoft Docs
description: 瞭解在 Visual Studio 偵錯工具中暫停執行時，如何回到呼叫 MFC 的函式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31bbb064aad5a43738b2f345cf31a20767c55e69
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384677"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>如何：如果暫止，回到呼叫 MFC 的函式

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

如果您使用 [偵錯] 功能表上的 [中斷] 命令來暫止程式並於 MFC 中結束，而且您確定問題位於程式碼時，可以使用 [呼叫堆疊] 視窗巡覽回該函式。 如需詳細資訊，請參閱 [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。

有時候，您的程式碼可能會在訊息幫浦內中斷。 如果發生這種情形，呼叫堆疊上不會有任何使用者程式碼。 若要避免發生此問題，您可以改用中斷點 (可能含條件與叫用次數) 來取代 [中斷] 命令。 如需詳細資訊，請參閱 [Breakpoints and Tracepoints](/previous-versions/ktf38f66(v=vs.100))。

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>流覽至從中呼叫 MFC 的函式

- 使用 [ **呼叫堆疊** ] 視窗。

## <a name="see-also"></a>另請參閱

- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)