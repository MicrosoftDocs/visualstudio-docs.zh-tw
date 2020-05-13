---
title: IEnum調試欄位::克隆 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1120e62d5dbed45f11b43ea0e131ee3173c1751c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716909"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
此方法將當前枚舉的副本作為單獨的物件返回。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]將此枚舉的副本作為單獨的物件返回。

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 枚舉的副本在調用此方法時與原始副本具有相同的狀態。 但是,副本和原始副本的狀態是分開的,可以單獨更改。

## <a name="see-also"></a>另請參閱
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
