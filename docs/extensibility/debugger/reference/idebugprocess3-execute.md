---
title: IDebugProcess3::Execute |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 349f792826bcfaa6ec3af1e10069e9c7182868bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
會繼續執行此程序，從停止的狀態。 清除任何先前的執行狀態 （例如步驟），並在處理序啟動重新執行。  
  
> [!NOTE]
>  應該使用這個方法，而不是[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表要執行的執行緒。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`，否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當使用者開始從某些其他處理序的執行緒處於停止狀態時執行時，此程序會呼叫這個方法。 當使用者選取時，也會呼叫這個方法**啟動**命令**偵錯**在 IDE 中的功能表。 這個方法的實作可能會只要呼叫[繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)程序中目前的執行緒上的方法。  
  
> [!WARNING]
>  不會停止事件或直接 （同步） 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫，否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)