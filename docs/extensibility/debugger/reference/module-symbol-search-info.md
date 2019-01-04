---
title: MODULE_SYMBOL_SEARCH_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e6bf29280345e1029a0732d36666ceba78ba2ed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826662"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
包含狀態資訊已搜尋的符號搜尋路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>參數  
 `dwValidFields`  
 從旗標的組合[SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)指定此結構中所述的搜尋資訊類型的列舉型別。  
  
 `bstrVerboseSearchInfo`  
 搜尋路徑，而且結果串連成單一字串。  
  
## <a name="remarks"></a>備註  
 此結構會從呼叫傳回[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)方法。  
  
 如果`bstrVerboseSearchInfo`欄位不是空的則它將包含路徑搜尋和該搜尋結果的清單。 路徑，後面接著省略符號 （"..."），後面接著結果會格式化為清單。 如果有多個路徑的結果組，每一組將分隔"\r\n"（歸位字元-/ 換行） 配對。 模式看起來像這樣：  
  
 \<路徑 >...\<結果 > \r\n\<路徑 >...\<結果 > \r\n\<路徑 >...\<結果 >  
  
 請注意最後一個項目沒有 \r\n 序列。  
  
 以下是可能`bstrVerboseSearchInfo`已傳送到標準輸出的字串。  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件：Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)