---
title: IDebugThread2::Resume |Microsoft Docs
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
ms.openlocfilehash: f41f26c824a779133a335c0d3d5080373b791d06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920985"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
繼續執行的執行緒。  
  
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
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 每個呼叫這個方法會遞減暫停計數到達 0 在哪個階段，實際繼續執行。 此暫停計數會顯示在**執行緒**偵錯視窗。  
  
 每次呼叫這個方法，必須是由先前呼叫[暫止](../../../extensibility/debugger/reference/idebugthread2-suspend.md)方法。 暫停計數決定多少次`IDebugThread2::Suspend`到目前為止已呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)