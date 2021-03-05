---
description: 新增埠。
title: IDebugPortSupplier2：： AddPort |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14232ac49b3862c635a41c25e79c7ab166fa24ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169232"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
新增埠。

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

## <a name="parameters"></a>參數
`pRequest`\
在描述要加入之埠的 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 物件。

`ppPort`\
擴展傳回表示埠的 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會實際建立要求的埠，以及將它新增至埠供應商的作用中埠的內部清單。 您可以先呼叫 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 方法，以避免可能耗用時間的延遲。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)
