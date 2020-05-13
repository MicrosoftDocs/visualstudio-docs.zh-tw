---
title: 程式控制 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738237"
---
# <a name="program-control"></a>程式控制
在 Visual Studio 除錯中,以下所有步進和持續例程都發生在程式等級:

- 設定下一個語句,即將電腦設置為要在特定幀環境中執行的下一個指令

- 執行,即繼續退出步進模式

- 步進下一個指令

- 繼續目前步進模式

- 掛起程式包含的線程

- 回復程式包含的線程

> [!NOTE]
> 查看調用堆疊是在線程級別實現的。 要枚舉線程的調用堆疊時枚舉幀資訊,必須實現[IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面的所有方法。

## <a name="methods-of-program-control"></a>程式控制方法
 下表顯示了為最小功能調試引擎 (DE) 和執行控制而必須實現的[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)方法。

|方法|描述|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|繼續運行程式從停止狀態包含的所有線程。 執行控制所需的。|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|繼續運行程式從停止狀態包含的所有線程。 執行控制所需的。|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|在給定的線程上執行步驟。 繼續運行程式包含的所有其他線程。 執行控制所需的。|

 對於多線程程式,還必須實現[IDebugProgram2:::enumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法以及[IEnum DebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md)介面的所有方法。

## <a name="see-also"></a>另請參閱
- [執行控制及狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
