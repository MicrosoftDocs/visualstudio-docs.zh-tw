---
title: IDebugTypeFieldBuilder2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 321004d1d0ef37597d477cff71435091a3123ccf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965638"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
擴充 **IDebugTypeFieldBuilder** ，以便能夠建立陣列類型。

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面可以從符號提供者取得。

## <a name="methods"></a>方法
 除了 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|建立指定型別和大小的陣列。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
