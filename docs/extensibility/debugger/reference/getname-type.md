---
title: GETNAME_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736669"
---
# <a name="getname_type"></a>GETNAME_TYPE
指定要檢索的檔案的名稱類型。

## <a name="syntax"></a>語法

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>欄位
`GN_NAME`\
指定文件或上下文的友好名稱。

`GN_FILENAME`\
指定文件或上下文的完整路徑。

`GN_BASENAME`\
指定基本檔名,而不是文檔或上下文的完整路徑。

`GN_MONIKERNAME`\
以名字物件的形式指定文檔或上下文的唯一名稱。

`GN_URL`\
指定文件或上下文的 URL 名稱。

`GN_TITLE`\
指定文件的標題(如果存在)。

`GN_STARTPAGEURL`\
獲取進程的起始頁網址。

## <a name="remarks"></a>備註
這些值作為參數傳遞給[GetName、GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)和[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)方法,以指定要返回的名稱類型。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
