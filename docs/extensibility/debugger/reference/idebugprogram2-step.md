---
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e153007fa8c60f17ca2e1ff09fb774b1e978bad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962858"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
會執行的步驟。  
  
> [!NOTE]
>  這個方法已淘汰。 使用[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示正在逐步執行的執行緒。  
  
 `sk`  
 [in]值，以從[STEPKIND](../../../extensibility/debugger/reference/stepkind.md)列舉，指定步驟的類型。  
  
 `step`  
 [in]值，以從[STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)列舉，指定步驟的單位 （例如，藉由陳述式或指令）。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果沒有任何執行緒同步處理或執行緒之間的通訊，當特定執行緒逐步執行時，就應該會執行中的其他執行緒。  
  
> [!WARNING]
>  不會傳送停止事件或即時 （同步） 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫; 否則為偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)