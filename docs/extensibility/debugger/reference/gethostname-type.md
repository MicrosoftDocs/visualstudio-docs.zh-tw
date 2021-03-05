---
description: 指定主機名稱的類型。
title: GETHOSTNAME_TYPE |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3354bdbceeac796e2761bb83a5d860ca8a716315
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150779"
---
# <a name="gethostname_type"></a>GETHOSTNAME_TYPE
指定主機名稱的類型。

## <a name="syntax"></a>Syntax

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="fields"></a>欄位
`GHN_FRIENDLY_NAME`\
指定主機的易記名稱。

`GHN_FILE_NAME`\
指定主控制項的檔案名。

## <a name="remarks"></a>備註
這些值會以引數的形式傳遞至 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) 方法，以取得不同格式的主機名稱。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
