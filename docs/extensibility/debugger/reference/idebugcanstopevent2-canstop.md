---
title: IDebugCanStopEvent2::CanStop |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3e2507ba86e00434c12a67ba70cad51fa5850ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
要在目前的程式碼位置停止或繼續執行，只會告知偵錯引擎 (DE)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fCanStop`  
 [in]非零 (`TRUE`) 如果 DE 應該停止在目前的程式碼位置; 否則為零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個事件的接收者通常會呼叫[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)方法，以判斷 DE 想要停止的原因，然後呼叫`IDebugCanStopEvent2::CanStop`方法與適當的回應。  
  
 如果 DE 停止時，它會傳送描述停止原因的事件。 通常有兩個事件，傳送時，由使用者或訊號中斷[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)介面，以及所代表的中斷點事件[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)