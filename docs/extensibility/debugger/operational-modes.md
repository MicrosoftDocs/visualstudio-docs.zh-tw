---
title: 操作模式 |Microsoft Docs
description: 深入瞭解 IDE 可以操作的三種模式，也就是設計模式、執行模式和中斷模式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cabf32dcbe8b4d2e925bcfd48635063ecd0a5b74
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606602"
---
# <a name="operational-modes"></a>操作模式
IDE 可以操作的模式有三種，如下所示：

- [設計模式](#vsconoperationalmodesanchor1)

- [執行模式](#vsconoperationalmodesanchor2)

- [中斷模式](#vsconoperationalmodesanchor3)

  您的自訂偵錯工具引擎 (在這些模式之間的轉換) 轉換，是需要您熟悉轉換機制的實作為決策。 DE 可能會或可能不會直接執行這些模式。 這些模式實際上是根據使用者動作或解除的事件來切換的封裝模式。 例如，從執行模式到中斷模式的轉換是由 DE 的停止事件所啟動。 從 break 轉換為執行模式或步驟模式的轉換，是由使用者執行作業（例如步驟或執行）所啟動。 如需有關取消轉換的詳細資訊，請參閱 [執行控制](../../extensibility/debugger/control-of-execution.md)。

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> 設計模式
 設計模式是 Visual Studio 偵錯工具的 nonrunning 狀態，在這段期間，您可以在應用程式中設定偵錯工具功能。

 在設計模式中，只會使用一些調試功能。 開發人員可以選擇設定中斷點或建立監看式運算式。 當 IDE 處於設計模式時，永遠不會載入或呼叫 DE。 與 DE 的互動只會在執行和中斷模式期間進行。

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> 執行模式
 在 IDE 的偵錯工具中執行程式時，會發生執行模式。 應用程式會在終止之前執行，直到遇到中斷點為止，或直到擲回例外狀況為止。 當應用程式執行結束時，會將取消轉換到設計模式。 當遇到中斷點或擲回例外狀況時，會將 DE 轉換成中斷模式。

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> 中斷模式
 當偵錯工具暫停執行時，就會發生中斷模式。 中斷模式為開發人員提供在中斷時應用程式的快照集，讓開發人員能夠分析應用程式的狀態，並變更應用程式的執行方式。 開發人員可以從相同的時間點，查看及編輯程式碼、檢查或修改資料、重新開機應用程式、結束執行或繼續執行。

 當取消傳送同步停止事件時，會進入中斷模式。 同步停止事件也稱為「停止事件」、通知會話 debug manager (SDM) 和正在進行偵錯工具的 IDE 已停止執行程式碼。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)介面是停止事件的範例。

 藉由呼叫下列其中一種方法來停止事件，會將偵錯工具從中斷模式轉換為執行或步驟模式：

- [執行](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [繼續](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> 步驟模式
 當程式逐步執行到下一行程式碼或進入、跳過或移出函式時，就會發生步驟模式。 藉由呼叫方法 [步驟](../../extensibility/debugger/reference/idebugprocess3-step.md)來執行步驟。 這個方法需要 `DWORD` 將 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 和 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 列舉指定為輸入參數的。

 當程式成功地逐步執行到下一行程式碼或進入函式時，或執行至資料指標或設定中斷點時，會自動轉換回中斷模式。

## <a name="see-also"></a>另請參閱
- [執行的控制](../../extensibility/debugger/control-of-execution.md)
