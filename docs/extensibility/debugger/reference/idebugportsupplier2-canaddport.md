---
description: 確認埠供應商可以新增埠。
title: IDebugPortSupplier2：： CanAddPort |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad704eda53807d344b23736d2d9b55e172c36468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072204"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
確認埠供應商可以新增埠。

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
 如果可以新增埠，則會傳回， `S_OK` 否則會傳回， `S_FALSE` 指出沒有任何埠可新增至此埠供應商。

## <a name="remarks"></a>備註
 呼叫這個方法之前，請先呼叫這個方法，然後再呼叫 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 方法，因為第二個方法會建立埠以及新增它，這可能是耗時的作業。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
