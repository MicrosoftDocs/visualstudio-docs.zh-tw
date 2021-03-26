---
title: 例外狀況處理 (Visual Studio SDK) |Microsoft Docs
description: 瞭解擲回例外狀況時所發生的進程。 本文說明所有相關步驟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f74337964b73683a71b180699da626121a4d3067
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097015"
---
# <a name="exception-handling-visual-studio-sdk"></a> (Visual Studio SDK) 的例外狀況處理
以下描述擲回例外狀況時所發生的進程。

## <a name="exception-handling-process"></a>例外狀況處理常式

1. 當第一次擲回例外狀況，但在要進行偵錯工具的程式中處理例外狀況處理常式之前，debug engine (DE) 會將 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 傳送至會話 debug MANAGER (SDM) 做為停止事件。 `IDebugExceptionEvent2`如果只有在偵錯工具封裝的 [例外狀況] 對話方塊中指定了例外狀況 (的設定，就會傳送，) 指定使用者想要在第一個可能發生的例外狀況通知時停止。

2. SDM 會呼叫 [IDebugExceptionEvent2：： GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) 來取得例外狀況的屬性。

3. Debug 封裝會呼叫 [IDebugExceptionEvent2：： CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 來判斷要向使用者呈現哪些選項。

4. 偵錯工具封裝會藉由開啟第一個可能的例外狀況對話方塊，要求使用者如何處理例外狀況。

5. 如果使用者選擇繼續，則 SDM 會呼叫 [IDebugExceptionEvent2：： CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)。

    - 如果方法傳回 S_OK，則會呼叫 [IDebugExceptionEvent2：:P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)。

         -或-

         如果方法傳回 S_FALSE，則會提供所要進行偵錯工具的第二次機會來處理例外狀況。

6. 如果正在進行程式設計的程式沒有第二次發生例外狀況的處理常式，則會將傳送 `IDebugExceptionEvent2` 至 SDM 做為 **EVENT_SYNC_STOP**。

7. 偵錯工具封裝會藉由開啟第一個可能的例外狀況對話方塊，要求使用者如何處理例外狀況。

8. Debug 封裝會呼叫 [IDebugExceptionEvent2：： CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 來判斷要向使用者呈現哪些選項。

9. Debug 封裝會要求使用者如何藉由開啟第二個例外狀況對話方塊來處理例外狀況。

10. 如果方法傳回 S_OK，則會呼叫 `IDebugExceptionEvent2::PassToDebuggee` 。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
