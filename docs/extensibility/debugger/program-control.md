---
title: "程式設計控制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 244f6c2113aef3b3c3576288a0c403d702d8b17a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="program-control"></a>程式控制權
在 Visual Studio 中偵錯所有下列逐步執行和繼續執行常式的層級發生程式：  
  
-   設定下一個陳述式，也就設定為要在特定畫面格的環境中執行的下一個指令的電腦  
  
-   結束 逐步執行模式執行，也就繼續  
  
-   逐步執行至下一個指令  
  
-   繼續目前的逐步執行模式  
  
-   暫止程式所包含的執行緒  
  
-   繼續執行程式所包含的執行緒  
  
> [!NOTE]
>  檢視呼叫堆疊上的執行緒層級實作。 若要檢視執行緒的呼叫堆疊時，列舉的畫面格的資訊，您必須實作所有方法的[IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面。  
  
## <a name="methods-of-program-control"></a>程式控制權的方法  
 下表顯示的方法[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ，必須使用最低限度功能偵錯引擎 (DE) 和執行控制實作。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|會繼續執行已停止狀態的程式所包含的所有執行緒。 執行控制項的必要項。|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|會繼續執行已停止狀態的程式所包含的所有執行緒。 執行控制項的必要項。|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|在給定的執行緒上執行的步驟。 會繼續執行其他程式所包含的所有執行緒。 執行控制項的必要項。|  
  
 對於多執行緒程式中，您也必須實作[IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法以及所有的方法[IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md)介面。  
  
## <a name="see-also"></a>請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)