---
title: IDebugClassField::EnumBaseClasses |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74889ed04dceb133c80467d20f723f9561b6e25c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703819"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
建立此類別的基底類別的列舉值。

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

#### <a name="parameters"></a>參數
 `ppEnum`

 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表基底類別清單。 如果沒有基底類別，則傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果沒有基底類別，則傳回 S_SH_NO_BASE_CLASSES (和`ppEnum`參數設為 null 的值)，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 中的列舉值物件的基底類別是以最立即可見的 （或最具衍生性的） 基底類別的大多數遠端的基底類別的順序指定。 例如，假設 c + + 類別：

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 列舉會傳回基底類別的順序`Level2`， `Level1`， `Root`。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)