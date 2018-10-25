---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 274610f84ff0447684eae6f5f728672d61aa08e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926159"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
取得[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)物件，描述為什麼中斷點未繫結的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetErrorBreakpoint(   
   IDebugErrorBreakpoint2** ppErrorBP  
);  
```  
  
```csharp  
int GetErrorBreakpoint(   
   out IDebugErrorBreakpoint2 ppErrorBP  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppErrorBP`  
 [out]傳回[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)描述警告或錯誤的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在後`IDebugErrorBreakpoint2`介面取得，請呼叫[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)方法來取得[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)物件。 然後[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法可用來判斷不正確的位置、 無效的運算式或為何暫止中斷點未繫結，例如，未載入的程式碼的原因，並依此類推。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CBreakpointSetDebugEventBase**公開 （expose） 的物件[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)介面。  
  
```cpp  
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(  
    IDebugErrorBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pError )  
        {  
            *ppbp = m_pError;  
  
            m_pError->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)