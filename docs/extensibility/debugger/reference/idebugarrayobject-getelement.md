---
title: IDebugarray物件:獲取元素 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736179"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
獲取陣列的元素。

## <a name="syntax"></a>語法

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>參數
`dwIndex`\
[在]元素索引。

`ppElement`\
[出]返回表示元素的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法將數位物件的所有元素視為一維陣列,即使陣組對像是多維的。 例如`myarray[3][2][6]`,給定陣列`dwIndex`和參數 20,此方法將從`myarray[1][1][2]`返回`dwIndex`元素 , 參數 21 將從返回 元素。 `myarray[1][1][3]` 使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)方法確定陣列中元素的總數。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
