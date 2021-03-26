---
description: 取得先前用來建立埠 (（如果可用) ）的埠描述。
title: IDebugPort2：： GetPortRequest |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77224f98d953b61529ffed083e7be4cee0ed662f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087479"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
取得先前用來建立埠 (（如果可用) ）的埠描述。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>參數
`ppRequest`\
擴展傳回 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 物件，代表用來建立埠的要求。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  `E_PORT_NO_REQUEST`如果未使用[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)埠要求建立埠，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
