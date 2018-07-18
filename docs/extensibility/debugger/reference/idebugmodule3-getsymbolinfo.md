---
title: IDebugModule3::GetSymbolInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53d84b9ef6cdabc12c88e30fc65d506cad673a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121023"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
擷取的路徑中搜尋符號，以及搜尋每個路徑的結果的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)指定哪些欄位的列舉型別`pInfo`會先填入。  
  
 `pInfo`  
 [out]A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)其成員的會利用指定的資訊填入的結構。 如果這是 null 值，這個方法會傳回`E_INVALIDARG`。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回`S_OK`; 否則它會傳回錯誤碼。  
  
> [!NOTE]
>  傳回的字串 (在`MODULE_SYMBOL_SEARCH_INFO`結構) 可能會空白即使`S_OK`會傳回。 在此情況下，沒有傳回任何搜尋資訊。  
  
## <a name="remarks"></a>備註  
 如果`bstrVerboseSearchInfo`欄位`MODULE_SYMBOL_SEARCH_INFO`結構不是空白，則它包含搜尋路徑和搜尋結果的清單。 包含的路徑，後面接著省略符號 （"…"），後面接著結果會格式化為清單。 如果有多個路徑的結果組，以"\r\n"（歸位字元位/換行） 配對區隔每個配對。 模式看起來像這樣：  
  
 \<路徑 >...\<結果 > \r\n\<路徑 >...\<結果 > \r\n\<路徑 >...\<結果 >  
  
 請注意最後一個項目沒有 \r\n 順序。  
  
## <a name="example"></a>範例  
 在此範例中，這個方法會傳回含有三個不同的搜尋結果的三個路徑。 復位/換行對以終止一行。 範例輸出只會列印以單一字串的搜尋結果。  
  
> [!NOTE]
>  狀態結果是後置 [...] 最多行結尾的所有項目。  
  
```cpp  
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
  
 **c:\symbols\user32.pdb...找不到檔案。**  
**c:\winnt\symbols\user32.pdb...版本不符。**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb...載入符號。**   
## <a name="see-also"></a>另請參閱  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)