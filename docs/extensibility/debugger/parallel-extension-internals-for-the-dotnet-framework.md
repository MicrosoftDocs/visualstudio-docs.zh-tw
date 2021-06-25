---
title: .NET Framework 的平行延伸模組內部 |Microsoft Docs
description: 這些資源會說明用來為 .NET Framework 平行擴充功能實作為自訂偵錯工具之類別的內部類型、方法和欄位。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 858bf85e65cd761e7f881856286578495db6143a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903004"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework 的平行延伸模組內部
本節說明類別的內部類型、方法和欄位，可協助您為 .NET Framework 的平行擴充功能，執行自訂偵錯工具。

## <a name="in-this-section"></a>本節內容
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md) 描述類別的內部資料成員 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 。

 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md) 描述類別的內部資料成員 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 。

 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md) 描述類別的內部資料成員 `System.Threading.Tasks.ContingentProperties` 。

 [AsyncTaskMethodBuilder 結構](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) 描述結構的內部成員 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 。

 [AsyncTaskMethodBuilder \<TResult> 結構](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) 描述結構的內部成員 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 。

 [AsyncVoidMethodBuilder 結構](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) 描述結構的內部成員 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 。

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [平行程式設計](/dotnet/standard/parallel-programming/index)
