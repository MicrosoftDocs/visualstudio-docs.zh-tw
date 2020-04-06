---
title: IDebugTypefieldBuilder2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718298"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
擴展**IDebugTypeFieldBuilder,** 以便能夠建立陣列類型。

## <a name="syntax"></a>語法

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>通話備註
 此介面可以從符號提供程序獲取。

## <a name="methods"></a>方法
 除了[IDebugTypeField Builder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|建立指定類型和大小的陣列。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
