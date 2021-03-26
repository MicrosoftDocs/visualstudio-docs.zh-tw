---
description: 本主題說明 CompilerServices. AsyncTaskMethodBuilder 類別的內部成員。
title: AsyncTaskMethodBuilder &lt; TResult &gt; 結構-內部成員 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 253d4fa79280fbb49ff0292121c0d0a5cfe4bdb2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055514"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; 結構-內部成員
本主題說明類別的內部成員 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 。 如需此類別的一般資訊，請參閱 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 參考主題。

 **命名空間：** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **元件：** mscorlib.dll) 中的 mscorlib (

 因為您無法從 .NET Framework 存取這些內部成員，所以會以一般中繼語言 () 的 CIL 來提供下列語法。

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>內部成員

|Name|描述|
|----------|-----------------|
|[>.objectidfordebugger 屬性](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|取得可用來唯一識別此產生器至偵錯工具的物件。|
|[m_task 欄位](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|表示延遲初始化的建立工作。|

## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [.NET Framework 的平行延伸模組內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
