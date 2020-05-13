---
title: m_children欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738421"
---
# <a name="m_children-field"></a>m_children欄位
在此任務中註冊的子任務的清單。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>備註
 當任務運行時,只有執行該任務的線程應訪問此陣組。

 如果任務已完成,則其他線程可以訪問此欄位,只要它們不向該欄位添加任何內容或從中刪除任何內容。

## <a name="see-also"></a>另請參閱
- [或有屬性類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)
