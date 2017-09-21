---
title: "IDebugPendingBreakpoint2::CanBind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::CanBind"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::CanBind 方法"
  - "CanBind 方法"
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::CanBind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

決定是否暫止中斷點可以繫結至程式碼的位置。  
  
## 語法  
  
```cpp#  
HRESULT CanBind (   
   IEnumDebugErrorBreakpoints2** ppErrorEnum  
);  
```  
  
```c#  
int CanBind (   
   out IEnumDebugErrorBreakpoints2 ppErrorEnum  
);  
```  
  
#### 參數  
 `ppErrorEnum`  
 \[\] out傳回[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)物件，其中包含一份[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)物件如果可能有錯誤。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK.` 會傳回`S_FALSE`如果中斷點無法繫結，在此情況下會傳回錯誤的`ppErrorEnum`參數。  否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果已刪除中斷點。  
  
## 備註  
 這個方法會呼叫來決定會發生什麼事情如果這暫止中斷點已繫結。  呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)實際繫結的暫止中斷點的方法。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CPendingBreakpoint`物件，公開 \(expose\) [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
```cpp#  
HRESULT CPendingBreakpoint::CanBind(IEnumDebugErrorBreakpoints2** ppErrorEnum)    
{    
   HRESULT hr;    
   HRESULT hrT;    
  
   // Check for a valid pointer to an error breakpoint enumerator   
   // interface; otherwise, return hr = E_INVALIDARG.    
   if (ppErrorEnum)    
   {    
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // Verify that the breakpoint is a file/line breakpoint.    
         if (IsFlagSet(m_pBPRequest->m_bpRequestInfo.dwFields, BPREQI_BPLOCATION) &&  
             m_pBPRequest->m_bpRequestInfo.bpLocation.bpLocationType == BPLT_CODE_FILE_LINE)    
         {    
            hr = S_OK;    
         }    
         // If the breakpoint type is not a file/line breakpoint, then the   
         // result should be an error breakpoint.    
         else    
         {    
            // If the error breakpoint member variable does not have   
            // allocated memory.  
            if (!m_pErrorBP)    
            {    
               // Create, AddRef, and initialize a CErrorBreakpoint object.    
               if (CComObject<CErrorBreakpoint>::CreateInstance(&m_pErrorBP) == S_OK)    
               {    
                  m_pErrorBP->AddRef();    
                  m_pErrorBP->Initialize(this);    
               }    
            }    
  
            // Create a new enumerator of error breakpoints.    
             CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;    
            if (CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum) == S_OK)    
            {    
               // Get the IDebugErrorBreakpoint2 information for the     
               // CErrorBreakpoint object.    
               CComPtr<IDebugErrorBreakpoint2> spErrorBP;    
               hrT = m_pErrorBP->QueryInterface(&spErrorBP);    
               assert(hrT == S_OK);    
               if (hrT == S_OK)    
               {    
                  // Initialize the new enumerator of error breakpoints   
                  // with the IDebugErrorBreakpoint2 information.      
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };    
                  hrT = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);    
                  if (hrT == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugErrorBreakpoints2     
                     // interface can be successful queried by the  
                     // created CEnumDebugErrorBreakpoints object.    
                     hrT = pErrorEnum->QueryInterface(ppErrorEnum);    
                     assert(hrT == S_OK);    
                  }    
               }    
  
               // Otherwise, delete the CEnumDebugErrorBreakpoints object.    
               if (FAILED(hrT))    
               {    
                  delete pErrorEnum;    
               }    
            }    
  
            hr = S_FALSE;    
         }    
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
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)