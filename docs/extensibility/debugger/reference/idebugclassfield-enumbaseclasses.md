---
description: 建立此類別之基類的列舉值。
title: IDebugClassField：： EnumBaseClasses |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ba31ead00ad2312b66273a2ddfaeebd252e0981
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084983"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
建立此類別之基類的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\

擴展傳回代表基類清單的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件。 如果沒有基底類別，則會傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果沒有基類 (且 `ppEnum` 參數設定為 null 值) ，則會傳回 S_SH_NO_BASE_CLASSES; 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉值物件中的基類是以最立即 (或最常衍生) 基類的順序指定，最多是遠端基類。 例如，假設 c + + 類別：

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 列舉會以 order `Level2` 、，傳回基類 `Level1` `Root` 。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
