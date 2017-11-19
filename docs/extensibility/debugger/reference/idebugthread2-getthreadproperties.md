---
title: "IDebugThread2::GetThreadProperties |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetThreadProperties
helpviewer_keywords: IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c118d8ccb4520cd63e2da91f0f807c7d6bc6ca8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
取得描述這個執行緒的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadProperties (   
   THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES*     ptp  
);  
```  
  
```csharp  
int GetThreadProperties (   
   enum_THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES[]         ptp  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)列舉，可判斷哪些欄位的`ptp`會先填入。  
  
 `ptp`  
 [in、 out]A [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構，填入這些執行緒的內容。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 從這個方法傳回的資訊通常會顯示在**執行緒**偵錯視窗。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CProgram`實作物件[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)介面。  
  
```cpp  
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,  
                                      THREADPROPERTIES *ptp)  
{  
    HRESULT hr = E_FAIL;    
  
    // Check for valid argument.    
   if (ptp)    
    {    
      // Create an array of buffers at ptp the size of the  
      // THREADPROPERTIES structure and set all of the  
      // buffers at ptp to 0.    
      memset(ptp, 0, sizeof (THREADPROPERTIES));    
  
      // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.    
      if (dwFields & TPF_ID)    
      {    
         // Check for successful assignment of the current thread ID to  
         //  the dwThreadId of the passed THREADPROPERTIES.    
         if (GetThreadId(&(ptp->dwThreadId)) == S_OK)    
         {    
            // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator    
            // of the passed THREADPROPERTIES.    
            ptp->dwFields |= TPF_ID;    
         }    
      }    
  
      hr = S_OK;    
    }    
    else    
        hr = E_INVALIDARG;    
  
    return hr;    
}    
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)