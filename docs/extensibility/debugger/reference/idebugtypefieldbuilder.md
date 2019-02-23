---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 456fe2656949e0cc862acdb97149b85f037beac8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720099"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
表示建立的欄位，表示類型的能力。

## <a name="syntax"></a>語法

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>呼叫端資訊
 這個介面被取自符號提供者。

## <a name="methods"></a>方法
 這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|建立表示基本類型的物件。|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|建立指定類型的指標。|

## <a name="requirements"></a>需求
 標頭：Sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll