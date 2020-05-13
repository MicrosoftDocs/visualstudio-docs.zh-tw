---
title: m_stateObject欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738368"
---
# <a name="m_stateobject-field"></a>m_stateObject欄位
表示操作將使用的數據的物件。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>備註
 這是構造函數`state`<xref:System.Threading.Tasks.Task.%23ctor%2A>中的 參數。 它也是屬性的<xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>後備欄位。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
