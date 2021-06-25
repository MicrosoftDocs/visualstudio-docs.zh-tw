---
title: 程式控制 |Microsoft Docs
description: 瞭解在程式層級進行 Visual Studio 偵錯工具中的常式，例如執行、逐步執行、繼續和暫停/繼續執行緒。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900705"
---
# <a name="program-control"></a>程式控制
在 Visual Studio 的偵錯工具中，會在程式層級進行下列所有逐步執行和繼續常式：

- 設定下一個語句，也就是將您的電腦設定為在特定框架環境下執行的下一個指令

- 執行中，也就是繼續退出逐步執行模式

- 逐步執行至下一個指令

- 繼續目前的逐步執行模式

- 暫停程式所包含的執行緒

- 繼續程式所包含的執行緒

> [!NOTE]
> 呼叫堆疊會線上程層級上執行。 若要在查看執行緒的呼叫堆疊時列舉框架資訊，您必須執行 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 介面的所有方法。

## <a name="methods-of-program-control"></a>程式控制項的方法
 下表顯示必須針對最小功能的 debug engine 所執行的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 方法 (DE) 和執行控制。

|方法|描述|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|繼續執行程式所包含的所有線程，從停止狀態。 執行控制權的必要參數。|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|繼續執行程式所包含的所有線程，從停止狀態。 執行控制權的必要參數。|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|在指定的執行緒上執行步驟。 繼續執行程式所包含的所有其他執行緒。 執行控制權的必要參數。|

 若為多執行緒程式，您也必須執行 [IDebugProgram2：： EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 方法和 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) 介面的所有方法。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
