---
title: IDebugStackFrame3：： InterceptCurrentException |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42472690431d48a9baafbb0abee27c1a07d24fcd
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "91403865"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

當偵錯工具想要攔截目前的例外狀況時，在目前的堆疊框架上呼叫它。  
  
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
 在指定不同的動作。 目前只支援 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) 值， `IEA_INTERCEPT` 而且必須指定。  
  
 `pqwCookie`  
 擴展識別特定例外狀況的唯一值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。  
  
 以下是最常見的錯誤傳回。  
  
|錯誤|描述|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|無法攔截目前的例外狀況。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|尚未在目前的執行框架中搜尋處理常式。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|此框架不支援這個方法。|  
  
## <a name="remarks"></a>備註  
 擲回例外狀況時，偵錯工具會在例外狀況處理常式期間，從執行時間取得控制權。 在這些按鍵期間，偵錯工具可以在框架想要攔截例外狀況時詢問目前的堆疊框架。 如此一來，攔截的例外狀況基本上是堆疊框架的即時例外狀況處理常式，即使該堆疊框架沒有例外狀況處理常式 (例如，程式碼中的 try/catch 區塊) 。  
  
 當偵錯工具想要知道是否應該攔截例外狀況時，它會在目前的堆疊框架物件上呼叫這個方法。 這個方法會負責處理例外狀況的所有詳細資料。 如果未執行 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) 介面或 `InterceptStackException` 方法傳回任何錯誤，則偵錯工具會繼續正常處理例外狀況。  
  
> [!NOTE]
> 例外狀況只能在 managed 程式碼中攔截，也就是當正在進行偵錯工具的程式是在 .NET 執行時間執行時。 當然，協力廠商語言實施者可以 `InterceptStackException` 在自己的偵錯工具引擎中執行，如果有的話，也可以選擇。  
  
 攔截完成之後， [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) 就會收到信號。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
