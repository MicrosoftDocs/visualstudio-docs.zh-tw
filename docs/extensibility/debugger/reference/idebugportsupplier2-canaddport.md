---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19eb4d11ab6e67384a119f11bf070a27159c1676
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871825"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
確認連接埠提供者可以新增新的連接埠。

## <a name="syntax"></a>語法

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>傳回值
 如果可以加入連接埠，會傳回`S_OK`; 否則傳回`S_FALSE`，表示沒有連接埠可以新增到此連接埠提供者。

## <a name="remarks"></a>備註
 呼叫這個方法，然後再呼叫[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)方法，因為第二個方法會建立連接埠，以及加入它，這可能耗時的作業。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)