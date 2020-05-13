---
title: IDebugPort供應商當地語系化2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98444ca60937d40262c92d89b8a6c48ed1a0b7ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724296"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
為埠供應商提供區域設置支援。

## <a name="syntax"></a>語法

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商實現此介面以設置區域設置。

## <a name="methods"></a>方法
 下表顯示了**IDebugPort供應商 Localee2**的方法。

|方法|描述|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|設置埠供應商的區域設置。|

## <a name="requirements"></a>需求
 標題: 波特普里夫.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
