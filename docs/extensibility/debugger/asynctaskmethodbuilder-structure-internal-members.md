---
title: AsyncTaskMethodBuilder 結構 - 內部成員
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 604f86311e2689d4301fec8a186e2a102d633062
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888429"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder 結構-內部成員
本主題說明類別的內部成員 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 。 如需此類別的一般資訊，請參閱 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> 參考主題。

 **命名空間：** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **元件：** mscorlib.dll) 中的 mscorlib (

 因為您無法從 .NET Framework 存取這些內部成員，所以會以一般中繼語言 () 的 CIL 來提供下列語法。

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>內部成員

|名稱|描述|
|----------|-----------------|
|[>.objectidfordebugger 屬性](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|取得可用來唯一識別此產生器至偵錯工具的物件。|
|[m_builder 欄位](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|表示這個非泛型實例所委派的一般 builder 物件。|

## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [.NET Framework 的平行延伸模組內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
