---
title: "IDebugComPlusSymbolProvider2::GetTypesByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypesByName"
  - "IDebugComPlusSymbolProvider2::GetTypesByName"
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider2::GetTypesByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取指定其名稱的型別。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetTypesByName(  
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetTypesByName(  
   string               pszClassName,  
   enum_ NAME_MATCH     nameMatch,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszClassName`  
 [in]型別的名稱。  
  
 `nameMatch`  
 [in]選取型的別相符項目，例如，區分大小寫。 介於 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 列舉型別。  
  
 `ppEnum`  
 [out]列舉值，其中包含具有指定名稱的類型。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 泛型型別，要尋找的名稱為 '清單 \< int>' 或 'List \< int、 int >' 「 清單 」。 如果具有相同名稱的類型會出現在多個模組， `ppEnum` 參數會包含所有複本。 您必須使用 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 和區分根據 `guidModule` 參數。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法的 **CDebugSymbolProvider** 公開物件 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) 介面。  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypesByName(  
    LPCOLESTR pszClassName,  
    NAME_MATCH nameMatch,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CModIter ModIter;  
    CModule* pmodule; // the iterator owns the reference  
    CFieldList listField;  
  
    ASSERT(IsValidWideStringPtr(pszClassName));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );  
  
    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    hr = S_FALSE;  
  
    if ( nameMatch == nmCaseInsensitive)  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,  
                    &listField,  
                    this ) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
    else  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByName( pszClassName,  
                                          &listField,  
                                          this) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
  
    // If the list is empty then no type  
    IfFalseGo( listField.GetCount(), E_FAIL );  
  
    // Create enumerator  
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)