---
title: IDebugPort供應商2::坎加德埠 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724756"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
驗證埠供應商是否可以添加新埠。

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
 如果可以新增連接埠,則傳`S_OK`回 。否則,返回`S_FALSE`以指示無法將任何埠添加到此埠供應商。

## <a name="remarks"></a>備註
 在調用[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)方法之前調用此方法,因為後一種方法創建埠並添加它,這可能是一項耗時的操作。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
