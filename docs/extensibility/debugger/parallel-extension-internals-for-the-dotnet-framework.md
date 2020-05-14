---
title: .NET 框架的並行擴展內部 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738268"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET 框架的並行擴展內部
本節介紹內部類型、方法和類欄位,這些類可説明您實現對 .NET 框架的並行擴展的自定義調試器。

## <a name="in-this-section"></a>本節內容
 [任務類](../../extensibility/debugger/task-class-internal-members.md)描述<xref:System.Threading.Tasks.Task?displayProperty=fullName>類的內部數據成員。

 [工作計劃器類](../../extensibility/debugger/taskscheduler-class-internal-members.md)描述<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類的內部數據成員。

 [或有屬性類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)描述`System.Threading.Tasks.ContingentProperties`類的內部數據成員。

 [非同步工作方法建構器結構](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)描述<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>結構的內部成員。

 [非同步任務方法建\<構器 TResult>结构](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)描述<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>結構的內部成員。

 [非同步VoidMethodBuilder結構](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)描述<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>結構的內部成員。

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [視覺化工作室除錯器可擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [平行編程式](/dotnet/standard/parallel-programming/index)
