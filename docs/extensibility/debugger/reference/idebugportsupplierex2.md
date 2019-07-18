---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bebf232e17df54d4dae2392a40f2ccbc3fc711c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353309"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
可讓您選取的工作並與其互動的核心伺服器連接埠提供者。

## <a name="syntax"></a>語法

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 自訂的連接埠提供者會實作這個介面，讓它可以選取要使用的核心伺服器。

## <a name="methods"></a>方法
 下表顯示的方法**IDebugPortSupplierEx2**。

|方法|描述|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|設定核心伺服器連接埠提供者。|

## <a name="requirements"></a>需求
 標頭：Portpriv.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)