---
title: AsyncTaskMethodBuilder 結構-內部成員 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f080e7a0fef7a03b878c253f09661338b5704df
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317635"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 結構-內部成員
本主題描述的內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>類別。 如需此類別的一般資訊，請參閱<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>參考主題。

 **命名空間︰** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **組件：** mscorlib （在 mscorlib.dll 中)

 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 (CIL)。

## <a name="syntax"></a>語法

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>內部成員

|名稱|描述|
|----------|-----------------|
|[ObjectIdForDebugger 屬性](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|取得物件，可用來唯一識別這個產生器偵錯工具。|
|[m_builder 欄位](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|表示這個非泛型執行個體將委派的泛型的產生器物件。|

## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [適用於.NET Framework 的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)