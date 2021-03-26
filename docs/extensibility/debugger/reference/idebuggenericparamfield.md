---
description: 代表 managed 程式碼泛型型別的參數。
title: IDebugGenericParamField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2dc01aaf3485e89ac32b4a4fd86c7491a1f96853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091925"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
代表 managed 程式碼泛型型別的參數。

## <a name="syntax"></a>Syntax

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 用於支援泛型。

## <a name="methods"></a>方法
 除了 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|傳回與這個泛型參數相關聯的條件約束數目。|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|捕獲與這個泛型參數相關聯的條件約束。|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|抓取這個泛型參數的旗標。|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|抓取這個泛型參數的索引。|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|抓取這個泛型參數的名稱。|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|抓取這個泛型參數的類型或方法擁有者。|

## <a name="requirements"></a>規格需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
