---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "IDebugSymbolProvider 介面"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示符號提供者所提供的符號和型別，將它們傳回的欄位。  
  
## 語法  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## 實作器注意事項  
 符號提供者必須實作這個介面來提供符號，而輸入的運算式評估工具的資訊。  
  
## 呼叫者的備忘稿  
 這個介面藉由使用 COM 的`CoCreateInstance`的功能 \(不受管理的符號提供者\)，或藉由載入適當的 managed 程式碼組件並具現化該組件中找到的資訊為基礎的符號提供者。  偵錯引擎會具現化的運算式評估工具搭配使用的符號提供者。  請參閱具現化這個介面的其中一個方法的範例。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugSymbolProvider`。  
  
|方法|描述|  
|--------|--------|  
|`Initialize`|已取代。  不要使用。|  
|`Uninitialize`|已取代。  不要使用。|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|取得包含偵錯的地址的欄位。|  
|`GetField`|已取代。  不要使用。|  
|[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)|對應到陣列的文件位置的偵錯的位址。|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|將文件內容對應至偵錯位址的陣列。|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|將偵錯位址對應到文件內容。|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|取得用來編譯偵錯的地址的程式碼的語言。|  
|`GetGlobalContainer`|已取代。  不要使用。|  
|[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)|取得表示完整的方法名稱的欄位。|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|取得表示完整的類別名稱的類別欄位型別。|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|會建立偵錯的地址相關聯的命名空間的列舉值。|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|符號名稱對應的符號型別。|  
|[GetNextAddress](../Topic/IDebugSymbolProvider::GetNextAddress.md)|取得偵錯位址後面指定偵錯中的地址的方法。|  
  
## 備註  
 這個介面會對應到偵錯的地址，或進行相反動作的文件位置。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 範例  
 本範例將示範如何具現化的符號提供者中，指定的 GUID \(偵錯引擎必須知道這個值\)。  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
  
## 請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)