---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25af7b2126be79901ceb97d6c93786d59111bfe1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703509"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
表示基本類型列舉值從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。

## <a name="syntax"></a>語法

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>方法
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|擷取這個欄位相關聯的基本類型。|

## <a name="requirements"></a>需求
 標頭：Sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll