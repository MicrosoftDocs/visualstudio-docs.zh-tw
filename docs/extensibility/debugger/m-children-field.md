---
description: 這項工作所註冊之子工作的清單。
title: m_children 欄位 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5aaf29d76a7bbd81a416c86360f315bc5c09b76c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158865"
---
# <a name="m_children-field"></a>m_children 欄位
這項工作所註冊之子工作的清單。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

 因為您無法從 .NET Framework 存取此內部成員，所以會在一般中繼語言 (的 CIL) 中提供下列語法。

## <a name="syntax"></a>語法

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>備註
 當工作正在執行時，只有執行工作的執行緒才能存取此陣列。

 如果工作已完成，其他執行緒就可以存取此欄位，只要它們不會在其中新增任何任何值，或從中移除任何檔案。

## <a name="see-also"></a>另請參閱
- [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)
