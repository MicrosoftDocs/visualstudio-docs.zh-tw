---
title: "IDebugBoundBreakpoint2::GetBreakpointResolution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetBreakpointResolution"
helpviewer_keywords: 
  - "GetBreakpointResolution 方法"
  - "IDebugBoundBreakpoint2::GetBreakpointResolution 方法"
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::GetBreakpointResolution
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得描述這個中斷點的中斷點解析度。  
  
## 語法  
  
```cpp#  
HRESULT GetBreakpointResolution(   
   IDebugBreakpointResolution2** ppBPResolution  
);  
```  
  
```c#  
int GetBreakpointResolution(   
   out IDebugBreakpointResolution2 ppBPResolution  
);  
```  
  
#### 參數  
 `ppBPResolution`  
 \[\] out傳回[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面，表示下列其中一項：  
  
-   描述程式碼的中斷點位置已繫結程式碼中之位置的中斷點解析物件。  
  
-   資料的位置已在繫結資料中斷點。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態會設定為`BPS_DELETED` \(屬於[BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別\)。  
  
## 備註  
 呼叫[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)方法，以判斷是否為程式碼或資料中斷點的解析度。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CBoundBreakpoint`物件，公開 \(expose\) [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
```  
HRESULT CBoundBreakpoint::GetBreakpointResolution(  
    IDebugBreakpointResolution2** ppBPResolution)  
{    
   HRESULT hr;    
  
   if (ppBPResolution)    
   {    
      // Verify that the bound breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugBreakpointResolution2 interface.    
         hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,  
                                       (void **)ppBPResolution);  
         assert(hr == S_OK);    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
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
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)