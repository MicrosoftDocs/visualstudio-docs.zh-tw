---
title: IDebugThread2::Resume |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f51fdb05fb44a23227a1a35fd6504f2d18aa804
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
繼續執行緒執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwSuspendCount`  
 [out]在繼續作業之後，傳回的暫停計數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個呼叫這個方法會暫停計數實際上直到它到達 0，此時，繼續執行。 此暫停計數會顯示在**執行緒**偵錯視窗。  
  
 每次呼叫此方法，必須是先前呼叫[暫停](../../../extensibility/debugger/reference/idebugthread2-suspend.md)方法。 暫停計數決定多少次`IDebugThread2::Suspend`到目前為止已呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)