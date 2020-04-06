---
title: 異常處理(可視化工作室 SDK) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738769"
---
# <a name="exception-handling-visual-studio-sdk"></a>例外處理(視覺化工作室 SDK)
下面描述了引發異常時發生的過程。

## <a name="exception-handling-process"></a>例外處理程序

1. 首次引發異常,但在調試程式中的異常處理程序處理異常之前,調試引擎 (DE) 會將[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)作為停止事件發送到會話調試管理器 (SDM)。 如果`IDebugExceptionEvent2`只被例外的設定(在除錯套件中的'例外'對話框中指定)指定使用者希望在首次機會異常通知時停止,則將發送 。

2. SDM 調用[IDebugexceptionEvent2::獲取異常](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)獲取異常屬性。

3. 調試包調用[IDebugexceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)以確定要向用戶呈現哪些選項。

4. 調試包詢問使用者如何通過打開第一個異常對話框來處理異常。

5. 如果使用者選擇繼續,SDM 將呼叫[IDebugexceptionevent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)。

    - 如果該方法返回S_OK,則調用[IDebugexceptionEvent2::PasstoDebuggee。](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)

         -或-

         如果方法返回S_FALSE,則正在調試的程式將第二次處理異常。

6. 如果正在除錯的程式沒有第二個例外的處理程式,則 DE`IDebugExceptionEvent2`將 a 傳送到 SDM 做**為 EVENT_SYNC_STOP**。

7. 調試包詢問使用者如何通過打開第一個異常對話框來處理異常。

8. 調試包調用[IDebugexceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)以確定要向用戶呈現哪些選項。

9. 調試包詢問使用者如何通過打開第二個異常對話框來處理異常。

10. 如果方法返回S_OK,則調用`IDebugExceptionEvent2::PassToDebuggee`。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
