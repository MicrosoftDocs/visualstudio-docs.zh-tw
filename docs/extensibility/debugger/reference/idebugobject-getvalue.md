---
title: IDebugObject::GetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e6fd1d3b4d7effe0f4c6f5f0434a01422345f00
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202885"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
取得物件的值做為一系列連續的位元組。

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
[in、 out]陣列，其中會填入一連串連續的位元組表示之物件的值。

`nSize`\
[in]要擷取的位元組數目上限。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 取得的值可以藉由呼叫擷取的位元組總數[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)