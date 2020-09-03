---
title: IDebugGenericParamField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727849"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
代表 managed 程式碼泛型型別的參數。

## <a name="syntax"></a>語法

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

## <a name="requirements"></a>需求
 標頭： Sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
