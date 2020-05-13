---
title: IDebug預設埠2::獲取埠通知 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732412"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
此方法獲取此埠的[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)介面。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>參數
`ppPortNotify`\
[出][IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 通常,在`QueryInterface`實現[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面的物件上調用該方法以獲取[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)介面。 但是,在某些情況下,所需的介面在不同的對象上實現。 此方法隱藏這些情況,`IDebugPortNotify2`並從最適當的物件返回介面。

## <a name="see-also"></a>另請參閱
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
