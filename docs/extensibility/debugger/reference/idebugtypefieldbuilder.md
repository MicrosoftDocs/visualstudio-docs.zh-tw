---
title: IDebugTypeFieldBuilder |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67a94f3f88d85d1e74ce7b1d67e1ef3d44546132
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965690"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
表示建立代表型別之欄位的能力。

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面是從符號提供者取得。

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|建立代表基本類型的物件。|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|建立指定類型的指標。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
