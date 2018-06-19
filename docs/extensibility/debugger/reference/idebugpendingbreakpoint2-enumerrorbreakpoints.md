---
title: IDebugPendingBreakpoint2::EnumErrorBreakpoints |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints
helpviewer_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints method
- EnumErrorBreakpoints method
ms.assetid: 2f9a9720-c1ac-4430-8f28-200d85360452
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bf419ccf3b0935dccf1fa4e56ec156bc4338da6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115323"
---
# <a name="idebugpendingbreakpoint2enumerrorbreakpoints"></a>IDebugPendingBreakpoint2::EnumErrorBreakpoints
取得導致此暫止中斷點的所有錯誤中斷點的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumErrorBreakpoints(   
   BP_ERROR_TYPE                 bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumErrorBreakpoints(   
   enum_BP_ERROR_TYPE              bpErrorType,  
   out IEnumDebugErrorBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bpErrorType`  
 [in]值組合[BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)選取要列舉的錯誤類型的列舉。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)物件，其中包含一份[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_BP_DELETED`若已刪除中斷點。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CPendingBreakpoint`公開物件[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
```cpp  
HRESULT CPendingBreakpoint::EnumErrorBreakpoints(  
   BP_ERROR_TYPE bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum)    
{    
   HRESULT hr;    
  
   // Verify that the passed IEnumDebugErrorBreakpoints2 interface pointer   
   // is valid.    
   if (ppEnum)    
   {    
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // Verify that this error is not a warning.    
         // All errors supported by this DE are errors, not warnings.    
         if (IsFlagSet(bpErrorType, BPET_TYPE_ERROR) && m_pErrorBP)    
         {    
            // Get the error breakpoint.    
            CComPtr<IDebugErrorBreakpoint2> spErrorBP;    
            hr = m_pErrorBP->QueryInterface(&spErrorBP);    
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Create the error breakpoint enumerator.    
               CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;    
               hr = CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum);    
               assert(hr == S_OK);    
               if (hr == S_OK)    
               {    
                  // Initialize the enumerator of error breakpoints with   
                  // the IDebugErrorBreakpoint2 information.      
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };    
                  hr = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);    
                  if (hr == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugErrorBreakpoints2     
                     // interface can be queried by the created   
                     // CEnumDebugErrorBreakpoints object.    
                     hr = pErrorEnum->QueryInterface(ppEnum);    
                     assert(hr == S_OK);    
                  }    
  
                  // Otherwise, delete the CEnumDebugErrorBreakpoints   
                  // object.    
                  if (FAILED(hr))    
                  {    
                     delete pErrorEnum;    
                  }    
               }    
            }    
         }    
         else    
         {    
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
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)