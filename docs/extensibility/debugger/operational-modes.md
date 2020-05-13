---
title: 操作模式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738289"
---
# <a name="operational-modes"></a>操作模式
IDE 可以操作三種模式,如下所示:

- [設計模式](#vsconoperationalmodesanchor1)

- [執行模式](#vsconoperationalmodesanchor2)

- [中斷模式](#vsconoperationalmodesanchor3)

  自定義調試引擎 (DE) 如何在這些模式之間轉換是一個實現決策,需要您熟悉轉換機制。 DE 可以直接實現這些模式,也可能不直接實現這些模式。 這些模式實際上是基於使用者操作或 DE 事件切換的調試包模式。 例如,從運行模式到中斷模式的過渡是由 DE 的停止事件引起的。 從中斷到運行模式或步進模式的過渡由執行操作(如步長或執行)的用戶發起。 有關 DE 轉換的詳細資訊,請參考[執行控制](../../extensibility/debugger/control-of-execution.md)。

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>設計模式
 設計模式是 Visual Studio 調試的非運行狀態,在此期間您可以在應用程式中設置調試功能。

 在設計模式下只使用幾個調試功能。 開發人員可以選擇設置斷點或創建監視表達式。 當 IDE 處於設計模式時,從不載入或調用 DE。 僅在運行和中斷模式下與 DE 互動。

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>執行模式
 當程式在 IDE 中的調試會話中運行時,將發生運行模式。 應用程式運行到終止,直到斷點被擊中,或直到引發異常。 當應用程式運行到終止時,DE將轉換為設計模式。 當斷點被擊中或引發異常時,DE 將轉換到中斷模式。

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>中斷模式
 暫停執行調試程式時,將發生中斷模式。 中斷模式為開發人員在中斷時提供應用程式的快照,並允許開發人員分析應用程式的狀態並更改應用程式的運行方式。 開發人員可以查看和編輯代碼、檢查或修改數據、重新啟動應用程式、結束執行或從同一點開始繼續執行。

 當 DE 發送同步停止事件時,將進入中斷模式。 同步停止事件(也稱為停止事件)通知會話調試管理員 (SDM) 和 IDE 正在調試的應用程式已停止執行代碼。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)介面是停止事件的示例。

 停止事件由呼叫以下方法之一繼續,這些方法之一將除錯器從中斷模式轉換為運行模式或步進模式:

- [執行](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [步驟](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [繼續](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>步進模式
 當程式步進下一行代碼或進入、越過或退出函數時,將發生步長模式。 步驟通過調用 方法[步驟](../../extensibility/debugger/reference/idebugprocess3-step.md)執行。 此方法需要`DWORD`指定[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)枚舉作為輸入參數的 s。

 當程式成功步進下一行代碼或函數,或運行到游標或設置的斷點時,DE 會自動轉換回中斷模式。

## <a name="see-also"></a>另請參閱
- [執行控制](../../extensibility/debugger/control-of-execution.md)
