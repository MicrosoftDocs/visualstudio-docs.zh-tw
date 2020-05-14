---
title: IDebug自定義屬性::獲取父項 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fae84a4d02438335aea00c50dd9b89520d08bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732696"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
獲取附加到自定義屬性的欄位。

## <a name="syntax"></a>語法

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
[出]返回表示自定義屬性附加到的欄位的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 在返回的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件上調用[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法,以確定父級欄位類型。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
