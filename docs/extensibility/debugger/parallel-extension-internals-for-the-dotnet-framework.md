---
title: 適用於.NET Framework 進行平行擴充內部資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0437363dd7d45b95a04a9e58edd45229f14b4c93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925358"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>適用於.NET Framework 的平行擴充內部資訊
本章節描述內部型別、 方法和欄位的類別可協助您實作自訂的 parallel extensions 到.NET Framework 偵錯工具。

## <a name="in-this-section"></a>本節內容
 [Task 類別](../../extensibility/debugger/task-class-internal-members.md)描述的內部資料成員<xref:System.Threading.Tasks.Task?displayProperty=fullName>類別。

 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)描述的內部資料成員<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類別。

 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)描述的內部資料成員`System.Threading.Tasks.ContingentProperties`類別。

 [AsyncTaskMethodBuilder 結構](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)描述的內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>結構。

 [AsyncTaskMethodBuilder\<TResult > 結構](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)描述的內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>結構。

 [AsyncVoidMethodBuilder 結構](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)描述的內部成員<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>結構。

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [平行程式設計](/dotnet/standard/parallel-programming/index)