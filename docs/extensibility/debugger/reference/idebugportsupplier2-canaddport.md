---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f4fd246c376d08ab3ca006c543b44c4db2d73d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340284"
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