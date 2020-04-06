---
title: MODULE_SYMBOL_SEARCH_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714249"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

包含有關已搜索的符號搜索路徑的狀態資訊。

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
[SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)枚舉中的標誌的組合,指定此結構中描述的搜索資訊類型。

`bstrVerboseSearchInfo`\
搜索路徑和結果串聯到單個字串中。

## <a name="remarks"></a>備註

此結構從對[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)方法的調用返回。

如果`bstrVerboseSearchInfo`該欄位不為空,則它包含搜索的路徑列表和該搜索的結果。 清單的格式採用路徑,後跟省略號 ("..."),後跟結果。 如果有多個路徑結果對,則每對由一對"\r\n"(回車/換行)對分隔。 模式如下所示:

\<路徑>...\<結果>\r\n\<路徑>...\<結果>\r\n\<路徑>...\<結果>

請注意,最後一個條目沒有 \r\n 序列。

下面是已發送到標準`bstrVerboseSearchInfo`出的可能的字串。

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>需求

標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
