---
title: IDebugMethodfield::EnumStaticLocals |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727149"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
為方法的靜態局部變數創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>參數
`ppLocals`\
[出]返回表示靜態局部變數清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有靜態局部變數,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE如果沒有靜態局部變數。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 每個元素都是一個[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件,表示不同類型的靜態局部變數。 調用每個物件上的[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法,以確定物件表示的靜態局部類型。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
