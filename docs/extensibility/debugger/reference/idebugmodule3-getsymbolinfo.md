---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "GetSymbolInfo 方法"
  - "IDebugModule3::GetSymbolInfo 方法"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取清單的路徑中搜尋符號，以及搜尋每個路徑的結果。  
  
## 語法  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### 參數  
 `dwFields`  
 \[\] in從旗標的組合 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 列舉指定的哪些欄位 `pInfo` 要進行填寫。  
  
 `pInfo`  
 \[\] outA [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 會利用指定的資訊填入其成員的結構。 如果這是 null 值，這個方法會傳回 `E_INVALIDARG`。  
  
## 傳回值  
 如果此方法成功，它會傳回 `S_OK`; 否則它會傳回錯誤碼。  
  
> [!NOTE]
>  傳回的字串 \(在 `MODULE_SYMBOL_SEARCH_INFO` 結構\) 可能是空的即使 `S_OK` 傳回。 在此情況下，沒有搜尋資訊來傳回。  
  
## 備註  
 如果 `bstrVerboseSearchInfo` 欄位 `MODULE_SYMBOL_SEARCH_INFO` 結構不是空白，則它將包含路徑搜尋和搜尋結果的清單。 清單會格式化為有一個路徑，後面接著省略符號 （"…"），後面接著結果。 如果有多個路徑的結果組，以"\\r\\n"（復位\/換行） 配對區隔每個組。 模式看起來像這樣︰  
  
 \< 路徑 \>...\< 結果 \> \\r\\n \< 路徑 \>...\< 結果 \> \\r\\n \< 路徑 \>...\< 結果 \>  
  
 請注意最後一個項目沒有 \\r\\n 順序。  
  
## 範例  
 在此範例中，這個方法會傳回三個路徑有三個不同的搜尋結果。 每一行會終止復位\/換行組中。 範例輸出只會搜尋結果列印以單一字串。  
  
> [!NOTE]
>  狀態結果是緊接"..."到該行結尾的所有項目。  
  
```cpp#  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\\symbols\\user32.pdb...找不到檔案。 c:\\winnt\\symbols\\user32.pdb...版本不符。 \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb...載入符號。**   
## 請參閱  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)