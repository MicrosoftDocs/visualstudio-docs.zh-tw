---
description: 以連續的位元組序列取得物件的值。
title: IDebugObject：： GetValue |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63e07ccfbcf2117363ed3e2096d5f0bb4bcac806
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150441"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
以連續的位元組序列取得物件的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>參數
`pValue`\
[in，out]以連續的位元組序列填入的陣列，代表物件的值。

`nSize`\
在要提取的最大位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 藉由呼叫 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) 方法，取得可提取的值位元組總數。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
