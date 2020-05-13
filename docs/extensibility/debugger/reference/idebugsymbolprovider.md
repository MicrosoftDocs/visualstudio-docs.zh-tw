---
title: IDebug符號提供者微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719179"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
此介面表示提供符號和類型的符號提供程式,將它們作為欄位返回。

## <a name="syntax"></a>語法

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
符號提供程式必須實現此介面,以便向表達式賦值器提供符號和鍵入資訊。

## <a name="notes-for-callers"></a>通話備註
此介面是透過使用 COM`CoCreateInstance`的功能 (對於非託管符號提供程式)或透過載入適當的託管代碼程式集並根據該程式集中的資訊實例化符號提供程式獲得的。 調試引擎實例化符號提供程式與運算式賦值器協調工作。 有關實例化此介面的一種方法,請參閱示例。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法`IDebugSymbolProvider`。

|方法|描述|
|------------|-----------------|
|`Initialize`|已被取代。 請勿使用。|
|`Uninitialize`|已被取代。 請勿使用。|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|獲取包含調試位址的欄位。|
|`GetField`|已被取代。 請勿使用。|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|將文件位置映射到調試位址陣列中。|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|將文件上下文映射到調試位址陣列中。|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|將調試位址映射到文檔上下文。|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|獲取用於在調試位址編譯代碼的語言。|
|`GetGlobalContainer`|已被取代。 請勿使用。|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|獲取表示完全限定方法名稱的欄位。|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|獲取表示完全限定類名稱的類欄位類型。|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|為與調試地址關聯的命名空間創建枚舉器。|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|將符號名稱映射到符號類型。|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|獲取方法中給定調試位址後面的調試位址。|

## <a name="remarks"></a>備註
此介面將文檔位置映射到調試位址,反之亦然。

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="example"></a>範例
此示例演示如何實例化符號提供程式(給定其 GUID(調試引擎必須知道此值)。

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
