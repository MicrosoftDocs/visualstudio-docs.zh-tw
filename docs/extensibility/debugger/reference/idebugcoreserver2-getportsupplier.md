---
description: 抓取特定的埠供應商。
title: IDebugCoreServer2：： GetPortSupplier |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPortSupplier
helpviewer_keywords:
- IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae0e60f1ff54c257ff3a71f694362152182454bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154739"
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
抓取特定的埠供應商。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortSupplier( 
   REFGUID               guidPortSupplier,
   IDebugPortSupplier2** ppPortSupplier
);
```

```csharp
int GetPortSupplier( 
   ref Guid                guidPortSupplier,
   out IDebugPortSupplier2 ppPortSupplier
);
```

## <a name="parameters"></a>參數
`guidPortSupplier`\
在要抓取之埠供應商的 GUID。

`ppPortSupplier`\
擴展傳回代表所需埠供應商的 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
