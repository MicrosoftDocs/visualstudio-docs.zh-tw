---
title: IDebug動態場+ |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 823057303655da59494680ce9f591b252e28f792
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731221"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
表示[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件的動態欄位。

## <a name="syntax"></a>語法

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>方法
 除了[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|檢索給定其基元類型的類型。|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|檢索給定其令牌的類型。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
