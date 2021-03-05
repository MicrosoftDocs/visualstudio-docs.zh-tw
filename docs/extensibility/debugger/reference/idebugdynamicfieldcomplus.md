---
description: 表示 IDebugBinder 物件的動態欄位。
title: IDebugDynamicFieldCOMPlus |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27fc3fb25b738db20d480a7a4542884dcb76123a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154026"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
表示 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 物件的動態欄位。

## <a name="syntax"></a>Syntax

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>方法
 除了 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|根據給定的基本型別來取得型別。|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|根據指定的權杖來抓取類型。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
