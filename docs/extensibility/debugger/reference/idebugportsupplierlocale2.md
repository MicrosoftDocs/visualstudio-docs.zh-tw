---
title: IDebugPortSupplierLocale2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2d59f46bdde06addf5454700eb45e64c3b452d78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874279"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
提供埠供應商的地區設定支援。

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂埠供應商會執行此介面來設定地區設定。

## <a name="methods"></a>方法
 下表顯示 **IDebugPortSupplierLocale2** 的方法。

|方法|描述|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|設定埠供應商的地區設定。|

## <a name="requirements"></a>規格需求
 標頭： Portpriv。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
