---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a87ec52c3c7929d32da2b568b8e2735efc6319d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917923"
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