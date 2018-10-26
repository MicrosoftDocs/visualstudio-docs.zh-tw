---
title: IDebugComPlusSymbolProvider2::FunctionHasLineInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FunctionHasLineInfo
- IDebugComPlusSymbolProvider2::FunctionHasLineInfo
ms.assetid: e1b508f1-6521-492f-b110-ab957744a037
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de6fb060e609907f89d7fc794d9d58a5e8c20186
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825124"
---
# <a name="idebugcomplussymbolprovider2functionhaslineinfo"></a>IDebugComPlusSymbolProvider2::FunctionHasLineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

判斷指定的方法是否具有行資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT FunctionHasLineInfo(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int FunctionHasLineInfo(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]所表示的偵錯位址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。 此位址必須是 METHOD_ADDRESS。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CDebugSymbolProvider**公開 （expose） 的物件[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)介面。  
  
```cpp#  
HRESULT CDebugSymbolProvider::FunctionHasLineInfo(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pAddress, E_INVALIDARG );  
  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->FunctionHasLineInfo( address.addr.addr.addrMethod.tokMethod,  
                                       address.addr.addr.addrMethod.dwVersion))  
    {  
  
        // S_FALSE indicates this method does not have line info  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)

