---
title: IDebug 擴展欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad10050aa157b4481fa2041ec5f322451983149f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729045"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
擴展可用於支援託管代碼泛型的欄位類型。

## <a name="syntax"></a>語法

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|檢索指定的擴展欄位類型。|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|確定該欄位是否表示閉合類型。|

## <a name="requirements"></a>需求
 標題: Sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
