---
title: IDebugBoundBreakpoint2::GetBreakpointResolution |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 19f668c9e71a5c5b31870b1a0d23a76a41b2d6b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
取得描述此中斷點的中斷點解析度。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBreakpointResolution(   
   IDebugBreakpointResolution2** ppBPResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugBreakpointResolution2 ppBPResolution  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppBPResolution`  
 [out]傳回[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)表示下列其中一種介面：  
  
-   描述程式碼中的，已經繫結程式碼中斷點位置的中斷點解析物件。  
  
-   資料的位置已在繫結資料中斷點。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態設定為`BPS_DELETED`(屬於[BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別)。  
  
## <a name="remarks"></a>備註  
 呼叫[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)方法，以判斷中斷點解析度是否為程式碼或資料。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CBoundBreakpoint`公開物件[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
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
  
## <a name="see-also"></a>請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)