---
title: 程式控制項 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 979a56740da506b51941211d5c6316a0614df142
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964544"
---
# <a name="program-control"></a>程式控制權
在 Visual Studio 中偵錯時，所有下列的逐步執行，並且繼續常式會執行的程式層級：  
  
-   設定下一個陳述式，也就設為您的電腦在特定畫面格的環境中執行的下一個指令  
  
-   結束 逐步執行模式執行，也就繼續  
  
-   逐步執行至下一個指令  
  
-   繼續進行目前的逐步執行模式  
  
-   暫止程式所包含的執行緒  
  
-   繼續執行程式所包含的執行緒  
  
> [!NOTE]
>  檢視呼叫堆疊被實作在執行緒層級上。 若要列舉的畫面格的資訊，檢視執行緒的呼叫堆疊時，您必須實作的所有方法[IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面。  
  
## <a name="methods-of-program-control"></a>程式控制項的方法  
 下表顯示的方法[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ，必須實作功能最小的偵錯引擎 (DE) 和執行控制。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|會繼續執行已停止狀態的程式所包含的所有執行緒。 執行控制項的必要項。|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|會繼續執行已停止狀態的程式所包含的所有執行緒。 執行控制項的必要項。|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|在指定的執行緒上執行的步驟。 會繼續執行其他程式所包含的所有執行緒。 執行控制項的必要項。|  
  
 對於多執行緒程式中，您必須同時實作[IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法及的所有方法[IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)