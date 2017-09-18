---
title: "MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO"
helpviewer_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO 結構"
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

包含狀態資訊中搜尋的符號搜尋路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```c#  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>參數  
 `dwValidFields`  
 從旗標的組合 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 指定此結構中所述的搜尋資訊類型的列舉型別。  
  
 `bstrVerboseSearchInfo`  
 搜尋路徑和結果串連成單一字串。  
  
## <a name="remarks"></a>備註  
 此結構會從呼叫傳回 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 方法。  
  
 如果 `bstrVerboseSearchInfo` 欄位不是空的則它將包含路徑搜尋和搜尋結果的清單。 清單會格式化為有一個路徑，後面接著省略符號 （"…"），後面接著結果。 如果有多個路徑的結果組，以"\r\n"（復位/換行） 配對區隔每個組。 模式看起來像這樣︰  
  
 \< 路徑>...\< 結果>\r\n \< 路徑>...\< 結果>\r\n \< 路徑>...\< 結果>  
  
 請注意最後一個項目沒有 \r\n 順序。  
  
 以下是可能發生 `bstrVerboseSearchInfo` 已傳送至標準輸出的字串。  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>需求  
 標頭︰ msdbg.h  
  
 命名空間 ︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件 ︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)