---
title: IDebugMethodField::枚舉 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727257"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
為調用方法所需的每個參數的類型創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>參數
`ppParams`\
[出]返回表示參數類型清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有參數,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE如果沒有參數。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 每個元素都是表示每個參數類型的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。 調用[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)方法以檢索有關每個參數類型的資訊。

 如果需要參數的名稱和類型,則調用[Enum 參數](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
