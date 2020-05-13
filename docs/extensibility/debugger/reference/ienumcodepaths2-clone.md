---
title: IEnumCodePath2::克隆 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Clone
helpviewer_keywords:
- IEnumCodePaths2::Clone
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ae54e34f316fb404a1ec125c3922584d7218bc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717879"
---
# <a name="ienumcodepaths2clone"></a>IEnumCodePaths2::Clone
將當前枚舉的副本作為單獨的物件返回。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumCodePaths2** ppEnum
);
```

```csharp
int Clone(
   out IEnumCodePaths2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]將此枚舉的副本作為單獨的物件返回。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 枚舉的副本在調用此方法時與原始副本具有相同的狀態。 但是,副本和原始副本的狀態是分開的,可以單獨更改。

## <a name="see-also"></a>另請參閱
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
