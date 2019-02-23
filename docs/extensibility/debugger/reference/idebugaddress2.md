---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10af641162fe9d254eaa3c0c2f5efbf841dc154e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677639"
---
# <a name="idebugaddress2"></a>IDebugAddress2
這個介面會提供給擁有之物件的位址的處理序識別碼的存取由這個介面。

## <a name="syntax"></a>語法

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者所實作的相同物件上實作這個介面[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。 這個介面會提供存取擁有的物件，這個地址相關的處理序的識別碼。

## <a name="notes-for-callers"></a>呼叫端資訊
 使用[QueryInterface](/cpp/atl/queryinterface)若要取得從這個介面[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。

## <a name="methods-in-vtable-order"></a>Vtable 順序中的方法
 除了繼承自方法[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|擷取擁有此介面所表示之物件的處理序識別碼。|

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)