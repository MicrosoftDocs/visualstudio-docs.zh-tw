---
title: IDebugCanStopEvent2：： GetReason |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191149"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得 debug engine (DE) 要停止的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcr`  
 擴展傳回 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 列舉中的值，這個值會描述這個事件的原因。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 通常會在 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 方法之前呼叫這個方法，讓呼叫端可以決定是否要將非零的 (`TRUE`) 傳遞給 `IDebugCanStopEvent2::CanStop` 方法。  
  
 停止的原因可能是，也 `CANSTOP_ENTRYPOINT` 就是 de 已到達進入點，或者 `CANSTOP_STEPIN` ，這表示已將 de 帶到函數中。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
