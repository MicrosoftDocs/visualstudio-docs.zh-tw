---
title: "IDebugBoundBreakpoint2::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetState"
helpviewer_keywords: 
  - "GetState 方法"
  - "IDebugBoundBreakpoint2::GetState 方法"
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得這個繫結中斷點的狀態。  
  
## 語法  
  
```cpp#  
HRESULT GetState(   
   BP_STATE* pState  
);  
```  
  
```c#  
int GetState(   
   out enum_BP_STATE pState  
);  
```  
  
#### 參數  
 `pState`  
 \[\] out傳回值，從[BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)將告訴您這個中斷點狀態的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CBoundBreakpoint`物件，公開 \(expose\) [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
```  
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)    
{    
   HRESULT hr;    
  
   // Check for a valid pointer to pState and assign the local state variable.    
   if (pState)    
   {    
      *pState = m_state;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## 請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)