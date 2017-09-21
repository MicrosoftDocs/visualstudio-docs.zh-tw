---
title: "IDebugCustomAttributeQuery::GetCustomAttributeByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery::GetCustomAttributeByName"
  - "GetCustomAttributeByName"
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCustomAttributeQuery::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取自訂屬性，指定其名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetCustomAttributeByName(  
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   string    pszCustomAttributeName,  
   ref int[] ppBlob,  
   out uint  pdwLen  
);  
```  
  
#### 參數  
 `pszCustomAttributeName`  
 \[in\]自訂屬性的名稱。  
  
 `ppBlob`  
 輸入 \[、 輸出\]包含自訂屬性資料的位元組陣列。  
  
 `pdwLen`  
 \[\] out以位元組為單位的長度`ppBlob`參數。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  如果自訂屬性不存在，會傳回`S_FALSE`。  否則，會傳回錯誤碼。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CDebugClassFieldSymbol** 物件，公開 \(expose\) [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)介面。  
  
```cpp#  
HRESULT CDebugClassFieldSymbol::GetCustomAttributeByName(  
    LPCOLESTR pszCustomAttributeName,  
    BYTE *pBlob,  
    DWORD *pdwLen  
)  
{  
    HRESULT hr = S_FALSE;  
    CComPtr<IMetaDataImport> pMetadata;  
    mdToken token = mdTokenNil;  
    CComPtr<IDebugField> pField;  
    CComPtr<IDebugCustomAttributeQuery> pCA;  
  
    ASSERT(IsValidWideStringPtr(pszCustomAttributeName));  
    ASSERT(IsValidWritePtr(pdwLen, ULONG*));  
  
    METHOD_ENTRY( CDebugClassFieldSymbol::GetCustomAttributeByName );  
  
    IfFalseGo( pszCustomAttributeName && pdwLen, E_INVALIDARG );  
  
    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );  
  
    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );  
    IfFailGo( CDebugCustomAttribute::GetCustomAttributeByName( pMetadata,  
              token,  
              pszCustomAttributeName,  
              pBlob,  
              pdwLen ) );  
Error:  
  
    METHOD_EXIT( CDebugClassFieldSymbol::GetCustomAttributeByName, hr );  
    return hr;  
}  
```  
  
## 請參閱  
 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)