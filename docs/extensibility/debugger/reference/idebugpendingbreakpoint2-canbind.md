---
title: IDebugPendingBreakpoint2::CanBind |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::CanBind
helpviewer_keywords:
- IDebugPendingBreakpoint2::CanBind method
- CanBind method
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e09bae8cfa6b4c2ba1b79ff74945e5256e23ed2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115719"
---
# <a name="idebugpendingbreakpoint2canbind"></a>IDebugPendingBreakpoint2::CanBind
決定是否此暫止中斷點可以繫結至程式碼位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanBind (   
   IEnumDebugErrorBreakpoints2** ppErrorEnum  
);  
```  
  
```csharp  
int CanBind (   
   out IEnumDebugErrorBreakpoints2 ppErrorEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppErrorEnum`  
 [out]傳回[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)物件，其中包含一份[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)物件 如果可能有錯誤。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK.`傳回`S_FALSE`中斷點無法繫結，如果在此情況下會傳回錯誤由`ppErrorEnum`參數。 反之則傳回錯誤碼。 傳回`E_BP_DELETED`若已刪除中斷點。  
  
## <a name="remarks"></a>備註  
 若要判斷時會發生什麼情況會呼叫這個方法如果這個暫止中斷點繫結。 呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)實際繫結暫止中斷點的方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CPendingBreakpoint`公開物件[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
```cpp  
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)