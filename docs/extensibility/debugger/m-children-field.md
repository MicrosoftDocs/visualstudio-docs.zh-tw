---
description: 這項工作所註冊之子工作的清單。
title: m_children 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901366"
---
# <a name="m_children-field"></a>m_children 欄位
這項工作所註冊之子工作的清單。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

 因為您無法從 .NET Framework 存取此內部成員，所以會在) 的通用中繼語言中提供下列語法 (。

## <a name="syntax"></a>語法

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>備註
 當工作正在執行時，只有執行工作的執行緒才能存取此陣列。

 如果工作已完成，其他執行緒就可以存取此欄位，只要它們不會在其中新增任何任何值，或從中移除任何檔案。

## <a name="see-also"></a>另請參閱
- [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)
