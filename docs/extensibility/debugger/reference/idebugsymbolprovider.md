---
title: IDebugSymbolProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8485497f9a5f0c6a04090755e6848bf8ed916ab3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909561"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
此介面代表提供符號和類型的符號提供者，並以欄位形式傳回它們。

## <a name="syntax"></a>Syntax

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
符號提供者必須執行這個介面，才能將符號和類型資訊提供給運算式評估工具。

## <a name="notes-for-callers"></a>呼叫者注意事項
您可以使用 COM 的函式 `CoCreateInstance` (針對未受管理的符號提供者) 或載入適當的 managed 程式碼元件，並根據在該元件中找到的資訊，將符號提供者具現化來取得這個介面。 Debug engine 會將符號提供者具現化，以配合運算式評估工具使用。 請參閱將此介面具現化的一個方法範例。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDebugSymbolProvider` 。

|方法|描述|
|------------|-----------------|
|`Initialize`|已取代。 請勿使用。|
|`Uninitialize`|已取代。 請勿使用。|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|取得包含此偵錯工具位址的欄位。|
|`GetField`|已取代。 請勿使用。|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|將檔位置對應至 debug 位址陣列。|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|將檔內容對應到一個 debug 位址陣列。|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|將 debug 位址對應至檔內容。|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|取得用來在偵錯工具位址編譯器代碼的語言。|
|`GetGlobalContainer`|已取代。 請勿使用。|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|取得代表完整方法名稱的欄位。|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|取得代表完整類別名稱的類別欄位類型。|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|建立與 debug 位址相關聯之命名空間的列舉值。|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|將符號名稱對應至符號類型。|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|取得在方法中指定的 debug 位址之後的偵錯工具位址。|

## <a name="remarks"></a>備註
這個介面會將檔位置對應至 debug 位址，反之亦然。

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>範例
這個範例會示範如何將符號提供者具現化，並指定其 GUID (debug engine 必須知道此值) 。

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
