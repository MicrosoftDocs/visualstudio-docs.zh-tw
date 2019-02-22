---
title: IDebugProcess3::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1b9dc08812722f843c091e1c87835377eb0621e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025315"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
讓逐步一指令或陳述式的處理序。  
  
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
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示正在逐步執行的執行緒。  
  
 `sk`  
 [in]其中一個[STEPKIND](../../../extensibility/debugger/reference/stepkind.md)值。  
  
 `step`  
 [in]其中一個[STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果沒有任何執行緒同步處理或執行緒之間的通訊，當特定的執行緒逐步執行時，就應該會執行程序中的其他執行緒。  
  
 **警告**不會傳送停止事件或即時 （同步） 事件，以[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫; 否則為偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)