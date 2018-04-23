---
title: IDebugProcess3::Step |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbc19c339e5d53bc9dde13ebd4a1bbddd214810c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
導致程序逐步執行一個指令或陳述式。  
  
> [!NOTE]
>  應該使用這個方法，而不是[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表要逐步執行的執行緒。  
  
 `sk`  
 [in]其中一個[STEPKIND](../../../extensibility/debugger/reference/stepkind.md)值。  
  
 `step`  
 [in]其中一個[STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 萬一有任何執行緒同步處理或執行緒之間的通訊，在特定執行緒逐步執行時，就應該會執行處理程序中的其他執行緒。  
  
 **警告**不會停止事件或直接 （同步） 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫，否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)