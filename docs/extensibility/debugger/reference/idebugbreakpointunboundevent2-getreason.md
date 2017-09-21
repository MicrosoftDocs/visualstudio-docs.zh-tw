---
title: "IDebugBreakpointUnboundEvent2::GetReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBreakpointUnboundEvent2::GetReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得中斷點是未繫結的原因。  
  
## 語法  
  
```cpp#  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```c#  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### 參數  
 `pdwUnboundReason`  
 \[\] out傳回值，從[BP\_UNBOUND\_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)列舉型別指定中斷點是未繫結的原因。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 原因包括正在不同的位置編輯後繼續作業或判斷，中斷點已繫結錯誤後重新繫結中斷點。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CBreakpointUnboundDebugEventBase** 物件，公開 \(expose\) [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)介面。  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(  
    BP_UNBOUND_REASON* pdwUnboundReason)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( EVAL(pdwUnboundReason) )  
    {  
        *pdwUnboundReason = m_dwReason;  
  
        hRes = S_OK;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## 請參閱  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)