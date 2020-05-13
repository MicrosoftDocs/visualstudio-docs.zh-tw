---
title: IDebug自定義屬性查詢2::枚舉屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732593"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
獲取附加到此欄位的所有自定義屬性的枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回表示自定義屬性清單的[IEnumDebugCustom 屬性](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)物件;否則,如果沒有自定義屬性,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK或S_FALSE如果此欄位上沒有自定義屬性。 否則,返回錯誤代碼;否則,將返回錯誤代碼。

## <a name="remarks"></a>備註
 欄位可以有多個自定義屬性。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
