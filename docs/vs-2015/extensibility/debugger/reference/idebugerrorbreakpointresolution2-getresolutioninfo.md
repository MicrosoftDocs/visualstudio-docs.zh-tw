---
title: IDebugErrorBreakpointResolution2::GetResolutionInfo |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
ms.assetid: d94c4f60-8796-4848-86ee-186bbaa613f5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79370105be84150f98a788e59c50367fbb68f1ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149004"
---
# <a name="idebugerrorbreakpointresolution2getresolutioninfo"></a>IDebugErrorBreakpointResolution2::GetResolutionInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得中斷點解析錯誤資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetResolutionInfo(   
   BPERESI_FIELDS            dwFields,  
   BP_ERROR_RESOLUTION_INFO* pErrorResolutionInfo  
);  
```  
  
```csharp  
int GetResolutionInfo(   
   enum_BPERESI_FIELDS        dwFields,  
   BP_ERROR_RESOLUTION_INFO[] pErrorResolutionInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)列舉型別，判斷哪些欄位`pErrorResolutionInfo`要填寫。  
  
 `pErrorResolutionInfo`  
 [in、 out][BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)會填入的中斷點解析描述的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例會實作這個方法來簡單`CDebugErrorBreakpointResolution`公開的物件[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)介面。  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetResolutionInfo(  
   BPERESI_FIELDS dwFields,  
   BP_ERROR_RESOLUTION_INFO* pBPErrorResolutionInfo)    
{    
   HRESULT hr;    
  
   if (pBPErrorResolutionInfo)    
   {    
      // Copy the specified fields of the request information from the class member  
      // variable to the local BP_ERROR_RESOLUTION_INFO variable.    
      hr = CopyBP_ERROR_RESOLUTION_INFO(m_bpErrorResolutionInfo,  
                                        *pBPErrorResolutionInfo,  
                                        dwFields);    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}  
  
HRESULT CDebugErrorBreakpointResolution::CopyBP_ERROR_RESOLUTION_INFO(  
   BP_ERROR_RESOLUTION_INFO& bpResSrc,  
   BP_ERROR_RESOLUTION_INFO& bpResDest,  
   DWORD dwFields)  
{    
   HRESULT hr = S_OK;    
  
   // Start with a raw copy.    
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_ERROR_RESOLUTION_INFO));    
  
   // The fields in the destination is the result of the AND of bpInfoSrc.dwFields  
   // and dwFields.    
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;    
  
   // Fill in the bp location information if the BPERESI_BPRESLOCATION flag  
   // is set in BPERESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_BPRESLOCATION))    
   {    
      // Switch on the BP_TYPE.      
      switch (bpResSrc.bpResLocation.bpType)    
      {    
         case BPT_CODE:    
         {    
            // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.    
            bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();    
            break;    
         }    
         case BPT_DATA:    
         {    
            // Copy the bstrDataExpr, bstrFunc, and bstrImage of the  
            // BP_RESOLUTION_DATA structure.    
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);  
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);  
            bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);  
            break;  
         }  
         default:  
         {  
            assert(FALSE);  
            // Clear the BPERESI_BPRESLOCATION flag of the BPERESI_FIELDS  
            // in the destination BP_ERROR_RESOLUTION_INFO.  
            ClearFlag(bpResDest.dwFields, BPERESI_BPRESLOCATION);  
            break;  
         }    
      }    
   }    
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_PROGRAM))    
   {    
      bpResDest.pProgram->AddRef();    
   }    
   // AddRef the IDebuThread2 if the BPRESI_THREAD flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_THREAD))    
   {    
      bpResDest.pThread->AddRef();    
   }    
   // Check if the BPERESI_MESSAGE flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_MESSAGE))    
   {    
      // Copy the source bstrMessage into the destination bstrMessage.    
      bpResDest.bstrMessage = SysAllocString(bpResSrc.bstrMessage);    
      // Clear the destination flag if there is no message.    
      if (!bpResDest.bstrMessage)    
      {    
         ClearFlag(bpResDest.dwFields, BPERESI_MESSAGE);    
      }    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
