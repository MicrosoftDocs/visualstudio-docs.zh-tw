---
title: IDebugGenericParamField |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727849"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
表示託管代碼泛型類型的參數。

## <a name="syntax"></a>語法

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>實施者說明
 用於支援泛型。

## <a name="methods"></a>方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|返回與此泛型參數關聯的約束數。|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|檢索與此泛型參數關聯的約束。|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|檢索此泛型參數的標誌。|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|檢索此泛型參數的索引。|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|檢索此泛型參數的名稱。|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|檢索此泛型參數的類型或方法擁有者。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
