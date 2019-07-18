---
title: MODULE_SYMBOL_SEARCH_INFO |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2cfbaf8c3756bf758956d1f1e5964d8e9f8f0c8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205189"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

包含狀態資訊已搜尋的符號搜尋路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
