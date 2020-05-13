---
title: 非同步虛無方法構建器結構 - 內部成員 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739294"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>非同步VoidMethodBuilder結構 - 內部成員
本主題介紹<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>類的內部成員。 有關此類的一般資訊,<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>請參閱參考主題。

 **命名空間:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **程式集**:mscorlib(在 mscorlib.dll 中)

 由於您無法從 .NET 框架訪問這些內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>內部成員

|名稱|描述|
|----------|-----------------|
|[物件 IdforDebugger 屬性](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|獲取可用於唯一標識調試器此生成器的物件。|
|[m_objectIdForDebugger欄位](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|表示調試器用於唯一標識此生成器的懶惰初始化物件。|

## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET 框架的並行擴展內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
