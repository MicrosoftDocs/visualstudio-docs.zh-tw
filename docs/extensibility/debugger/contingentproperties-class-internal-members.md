---
title: 或有屬性類 - 內部成員 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739108"
---
# <a name="contingentproperties-class---internal-members"></a>或有屬性類別 ─內部成員
包含<xref:System.Threading.Tasks.Task>物件的其他屬性。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在 mscorlib.dll 中)

 由於您無法從 .NET 框架訪問這些內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>成員

### <a name="fields"></a>欄位

|名稱|描述|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|在此任務中註冊的子任務的清單。|

## <a name="remarks"></a>備註
 .NET 框架僅在需要此類欄位時初始化。

## <a name="see-also"></a>另請參閱
- [.NET 框架的並行擴展內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
