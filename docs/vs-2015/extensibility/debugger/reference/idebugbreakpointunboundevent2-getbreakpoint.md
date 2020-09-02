---
title: IDebugBreakpointUnboundEvent2：： GetBreakpoint |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11640da3bcf5ad25aced8bee6fd6d981d658a772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160059"
---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得變成未系結的中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetBreakpoint(   
   IDebugBoundBreakpoint2** ppBP  
);  
```  
  
```csharp  
int GetBreakpoint(   
   out IDebugBoundBreakpoint2 ppBP  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppBP`  
 擴展傳回代表已解除系結之中斷點的 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何針對公開[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)介面的**CBreakpointUnboundDebugEventBase**物件，執行這個方法。  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(  
    IDebugBoundBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pbp )  
        {  
            IDebugBoundBreakpoint2 *pibp;  
  
            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);  
  
            if ( S_OK == hRes )  
                *ppbp = pibp;  
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
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
