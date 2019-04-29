---
title: IDebugPortSupplier2::AddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c674b73ad6ec45b1e388f62fbd3103afb5daedb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918107"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
新增連接埠。

## <a name="syntax"></a>語法

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

#### <a name="parameters"></a>參數
 `pRequest`

 [in][IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)物件，描述要加入的連接埠。

 `ppPort`

 [out]傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示連接埠。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法實際上會建立要求的通訊埠，以及將它新增至作用中的連接埠的連接埠提供者的內部清單。 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)可以先呼叫方法，以避免可能耗費時間的延遲。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)