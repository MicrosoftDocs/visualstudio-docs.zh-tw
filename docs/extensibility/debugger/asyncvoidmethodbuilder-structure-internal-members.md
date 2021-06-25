---
description: 本主題說明 CompilerServices. AsyncVoidMethodBuilder 類別的內部成員。
title: AsyncVoidMethodBuilder 結構-內部成員 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6606e26d14ba114ed8346c0cc11a81f8bdd3e8e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903629"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder 結構-內部成員
本主題說明類別的內部成員 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 。 如需此類別的一般資訊，請參閱 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 參考主題。

 **命名空間：** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **元件：** mscorlib.dll) 中的 mscorlib (

 因為您無法從 .NET Framework 存取這些內部成員，所以會以一般中繼語言 () 的 CIL 來提供下列語法。

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>內部成員

|Name|描述|
|----------|-----------------|
|[>.objectidfordebugger 屬性](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|取得可用來唯一識別此產生器至偵錯工具的物件。|
|[m_objectIdForDebugger 欄位](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|表示偵錯工具用來唯一識別此產生器的延遲初始化物件。|

## <a name="see-also"></a>另請參閱
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET Framework 的平行延伸模組內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
