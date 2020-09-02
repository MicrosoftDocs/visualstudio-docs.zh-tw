---
title: IDebugBeforeSymbolSearchEvent2：： GetModuleName |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff2f20e722e8e4870bce1c5bc7d10d70033026
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423567"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

抓取目前正在進行調試的模組名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetModuleName(   
   BSTR *pbstrModuleName  
);  
```  
  
```csharp  
public int GetModuleName (  
   string pbstrModuleName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrModuleName`  
 擴展模組的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何針對公開[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)介面的**CDebugBeforeSymbolSearchEventBase**物件，執行這個方法。  
  
```cpp#  
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (m_bstrModuleName)  
    {  
  
        *pbstrModuleName = SysAllocString( m_bstrModuleName);  
  
        if (*pbstrModuleName)  
        {  
            hRes = S_OK;  
        }  
    }  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)
