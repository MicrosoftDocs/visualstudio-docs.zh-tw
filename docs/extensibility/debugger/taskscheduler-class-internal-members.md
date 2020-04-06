---
title: 任務計劃員類 - 內部成員 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712571"
---
# <a name="taskscheduler-class---internal-members"></a>工作計劃器類別 ─ 內部成員
本文介紹了説明您實現自定義調試器的<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類的內部成員。 有關此類的一般資訊,<xref:System.Threading.Tasks.TaskScheduler>請參閱參考文章。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問這些內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|----------|-----------------|
|[取得除錯器的排程工作](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|檢索所有計劃任務的陣列。|
|[取得工作計劃對除錯器](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|檢索當前處於活動狀態的所有<xref:System.Threading.Tasks.TaskScheduler>物件的陣列。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET 框架的並行擴展內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
