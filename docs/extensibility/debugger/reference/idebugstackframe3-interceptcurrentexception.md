---
title: IDebugStackFrame3::InterceptCurrentException |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d46ae2f3ae0c63c798fc42b93d50e5aee398ccf5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
目前的堆疊框架上偵錯工具在其想要攔截目前的例外狀況時呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFlags`  
 [in]指定不同的動作。 目前，只有[INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)值`IEA_INTERCEPT`支援，而且必須指定。  
  
 `pqwCookie`  
 [out]識別特定的例外狀況的唯一值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
 以下是最常見的錯誤傳回。  
  
|錯誤|描述|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|無法攔截目前的例外狀況。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|目前的執行框架尚未尚未搜尋處理常式。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|這個方法不支援這個畫面格。|  
  
## <a name="remarks"></a>備註  
 擲回例外狀況時，偵錯工具會從取得控制的關鍵點在執行階段期間的例外狀況處理程序。 在這些索引鍵的時間，偵錯工具可以要求目前的堆疊框架框架是否要攔截的例外狀況。 如此一來，攔截的例外狀況是基本上上即時例外狀況處理常式的堆疊框架，即使該堆疊框架沒有例外處理常式 （例如，try/catch 區塊中的程式碼）。  
  
 當偵錯工具想要知道是否應該攔截例外狀況時，它會在目前的堆疊框架物件上呼叫這個方法。 這個方法會負責處理所有例外狀況的詳細資料。 如果[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)未實作介面或`InterceptStackException`方法會傳回任何錯誤，則偵錯工具會繼續正常處理例外狀況。  
  
> [!NOTE]
>  例外狀況可以被攔截只在 managed 程式碼，也就是以.NET 執行階段執行所偵錯的程式時。 當然，可以實作協力廠商語言實作者`InterceptStackException`人員可以選擇他們自己的偵錯引擎中。  
  
 攔截完成之後， [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)收到信號。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)