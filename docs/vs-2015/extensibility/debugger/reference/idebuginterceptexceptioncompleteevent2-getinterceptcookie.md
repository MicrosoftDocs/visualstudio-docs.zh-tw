---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc8f5c2172263590839194437c41108ef8fb23a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858403"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

攔截到例外狀況處理完成時呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pqwCookie`  
 [out]攔截到例外狀況相關聯的唯一值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在後[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)方法已完成之攔截的例外狀況處理，它會傳送[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)事件。 可以使用處理常式`GetInterceptCookie`方法來擷取例外狀況相關聯的唯一值 (相同的值傳遞至`InterceptCurrentException`方法)。  
  
## <a name="see-also"></a>另請參閱  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

