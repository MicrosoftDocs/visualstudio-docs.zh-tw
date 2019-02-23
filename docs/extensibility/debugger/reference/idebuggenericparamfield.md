---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab5cb19475ae92ab1e89bdce5c833e0f18a2cccb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720702"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
表示 managed 程式碼的泛型類型參數。

## <a name="syntax"></a>語法

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>實作者的附註
 用於泛型的支援。

## <a name="methods"></a>方法
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|傳回與此泛型參數相關聯的條件約束的數目。|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|擷取此泛型參數相關聯的條件約束。|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|擷取此泛型參數的旗標。|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|擷取此泛型參數的索引。|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|擷取此泛型參數的名稱。|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|擷取此泛型參數的型別或方法擁有者。|

## <a name="requirements"></a>需求
 標頭：Sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll