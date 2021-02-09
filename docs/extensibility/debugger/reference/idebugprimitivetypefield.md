---
title: IDebugPrimitiveTypeField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65ebc0a4c029cdb748ebfadff41f83d0cbb2ab75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874187"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
表示來自 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面的基本類型列舉值。

## <a name="syntax"></a>Syntax

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>方法
 除了 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|抓取與此欄位相關聯的基本類型。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
