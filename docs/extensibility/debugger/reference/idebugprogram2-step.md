---
title: IDebugProgram2::Step |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10685adb27c9bf2e962beccb7e68f19ce5c27eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
會執行步驟。  
  
> [!NOTE]
>  這個方法已被取代。 使用[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法改為。  
  
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
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表要逐步執行的執行緒。  
  
 `sk`  
 [in]中的值[STEPKIND](../../../extensibility/debugger/reference/stepkind.md)列舉，指定步驟的類型。  
  
 `step`  
 [in]中的值[STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)列舉，指定步驟的單位 （例如，陳述式所指示）。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 萬一有任何執行緒同步處理或執行緒之間的通訊，當特定的執行緒逐步執行時，就應該會執行程式中的其他執行緒。  
  
> [!WARNING]
>  不會停止事件或直接 （同步） 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫，否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)