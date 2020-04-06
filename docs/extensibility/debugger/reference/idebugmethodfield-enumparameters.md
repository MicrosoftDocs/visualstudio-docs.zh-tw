---
title: IDebugMethodField:枚舉參數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727191"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
為方法的參數創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>參數
`ppParams`\
[出]返回表示方法參數清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件;否則,如果沒有參數,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或返回S_FALSE如果沒有參數。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 每個元素都是表示不同類型的參數的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。 調用每個物件上的[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法,以確定物件表示的參數類型。

 參數包括其變數名稱和類型。 類別的參數通常是「this」指標。

 如果只需要參數的類型,請調用[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
