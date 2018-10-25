---
title: IDebugComPlusSymbolProvider2::IsAddressSequencePoint |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::IsAddressSequencePoint
- IsAddressSequencePoint
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec0aefd8f59793fdd555ff0cc14f767c10e8972a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829907"
---
# <a name="idebugcomplussymbolprovider2isaddresssequencepoint"></a>IDebugComPlusSymbolProvider2::IsAddressSequencePoint
判斷指定的偵錯位址為序列點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsAddressSequencePoint(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsAddressSequencePoint(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]偵錯所表示的地址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果偵錯位址都是序列點，會傳回`S_OK`; 否則傳回`S_FALSE`。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CDebugSymbolProvider**公開 （expose） 的物件[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)介面。  
  
```cpp  
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(  
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
  
    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,  
                                   address.addr.addr.addrMethod.dwVersion,  
                                   address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this is not a sequence point  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)