---
title: IDebugObject:獲取價值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726550"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
獲取物件的值作為連續位元組系列。

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
[進出]用表示物件值的連續位元組系列填充的陣列。

`nSize`\
[在]要提取的最大位元組數。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 通過調用[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)方法獲取可以提取的值位元組的總數。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
