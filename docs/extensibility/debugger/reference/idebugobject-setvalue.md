---
title: IDebugObject:設定值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726364"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
設置連續位元組序列中物件的值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>參數
`pValue`\
[在]表示新值的位元組。

`nSize`\
[在]值的大小(以位元組為單位)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 陣列中的值將複製到此[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)中,替換任何現有值。 新值的大小可以大於或小於現有值。 這`IDebugObject`不能為空引用。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
