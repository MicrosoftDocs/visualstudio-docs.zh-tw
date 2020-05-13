---
title: 執行控制 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739070"
---
# <a name="control-of-execution"></a>執行控制
除錯引擎 (DE) 通常作為上次啟動事件傳送以下事件之一:

- 入口點事件(如果附加到新啟動的程式)

- 負載完成事件(如果附加到已執行的程式)

  這兩個事件都停止事件,這意味著 DE 通過 IDE 等待使用者的回應。 有關詳細資訊,請參閱[操作模式](../../extensibility/debugger/operational-modes.md)。

## <a name="stopping-event"></a>停止事件
 當停止事件傳送到除錯工作階段時:

1. 可以從事件介面獲取包含當前指令指標的程式和線程。

2. IDE 確定目前原始程式碼檔和位置,該檔和位置在編輯器中顯示為突出顯示。

3. 除錯工作階段通常透過呼叫程式的 **「繼續」** 方法回應此第一個停止事件。

4. 然後,程式運行,直到它遇到停止條件,如擊中斷點。 在這種情況下,DE 向調試會話發送斷點事件。 斷點事件是停止事件,DE 再次等待用戶回應。

5. 如果用戶選擇踏入、執行或退出函數,IDE 會提示調試會話調用`Step`程式 的方法。 然後,IDE 傳遞步進單元(指令、語句或行)和步進類型(是步進、執行還是退出函數)。 步驟完成後,DE 會向調試會話發送一個步驟完成事件,調試會話是停止事件。

    -或-

    如果使用者選擇繼續從目前的指令指標執行,IDE 會提示除錯工作階段呼叫**程式的執行方法**。 程序恢復執行,直到遇到下一個停止條件。

    -或-

    如果調試會話要忽略特定的停止事件,則調試會話將調用程式的 **"繼續"** 方法。 如果程式在遇到停止條件時步進、越過或退出函數,則繼續執行此步驟。

   在程式設計上,當 DE 遇到停止條件時,它會透過[IDebugEvent 回檔 2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面向工作階段調試管理員 (SDM) 傳送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)等停止事件。 DE 傳遞[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)和[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)介面,這些介面表示程式和包含當前指令指標的線程。 SDM 調用[IDebugThread2:enumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)獲取頂部堆疊幀,並調用[IDebugStackFrame2:::獲取文檔上下文](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)以獲取有關當前指令指標的文檔上下文。 此文件上下文通常是原始碼檔名、行號和列號。 IDE 使用這些突出顯示包含當前指令指標的原始程式碼。

   SDM 通常通過調用[IDebugProgram2::繼續](../../extensibility/debugger/reference/idebugprogram2-continue.md)來回應第一個停止事件。 然後,程式運行,直到它遇到停止條件,如擊中斷點,在這種情況下,DE 向 SDM 發送[IDebugBreakpointEvent2 介面](../../extensibility/debugger/reference/idebugbreakpointevent2.md)。 斷點事件是停止事件,DE 再次等待用戶回應。

   如果使用者選擇踏入、執行或退出函數,IDE 將提示 SDM 呼叫[IDebugProgram2::步驟](../../extensibility/debugger/reference/idebugprogram2-step.md)。 然後,IDE 傳遞[STEPUNIT(](../../extensibility/debugger/reference/stepunit.md)指令、語句或行)和[STEPKIND,](../../extensibility/debugger/reference/stepkind.md)即是步進、執行還是退出函數。 步驟完成後,DE 會向 SDM 發送[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)介面,這是一個停止事件。

   如果使用者選擇繼續從目前的指令指標執行,IDE 會要求 SDM 呼叫[IDebugProgram2:::執行](../../extensibility/debugger/reference/idebugprogram2-execute.md)。 程序恢復執行,直到遇到下一個停止條件。

   如果除錯套件要忽略特定的停止事件,除錯套件將呼叫 SDM,它呼叫[IDebugProgram2:::繼續](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 如果程式在遇到停止條件時步進、執行或退出函數,則繼續執行此步驟。 這意味著程式保持步進狀態,以便它知道如何繼續。

   SDM`Step`對**的調用**是**Continue**非同步的,這意味著 SDM 希望調用快速返回。 如果 DE 在執行 **「或****」繼續**返回「`Step`之前在同一線程上向 SDM 發送停止事件,則 SDM 掛起。

## <a name="see-also"></a>另請參閱
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
