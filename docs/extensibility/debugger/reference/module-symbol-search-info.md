---
description: 包含已搜尋之符號搜尋路徑的相關狀態資訊。
title: MODULE_SYMBOL_SEARCH_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 266d786df422e5260e212a4005feb7d3167af099
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057893"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

包含已搜尋之符號搜尋路徑的相關狀態資訊。

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

## <a name="members"></a>成員

`dwValidFields`\
[SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)列舉中的旗標組合，指定此結構中所描述的搜尋資訊種類。

`bstrVerboseSearchInfo`\
搜尋路徑和結果串連成單一字串。

## <a name="remarks"></a>備註

從呼叫 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 方法時，會傳回這個結構。

如果 `bstrVerboseSearchInfo` 欄位不是空的，則會包含搜尋的路徑清單以及該搜尋的結果。 此清單的格式為路徑，後面接著省略號 ( "..." ) ，後面接著結果。 如果有一個以上的路徑結果配對，則每一組都會以 "\r\n" (換行字元) 組分隔。 模式看起來像這樣：

\<path>...\<result>\r\n \<path> \<result> .。。\r\n \<path> .。。\<result>

請注意，最後一個專案沒有 \r\n 順序。

以下是已 `bstrVerboseSearchInfo` 傳送至標準輸出的可能字串。

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>規格需求

標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
