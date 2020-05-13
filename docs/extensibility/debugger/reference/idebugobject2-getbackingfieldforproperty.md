---
title: IDebugObject2::獲取屬性的"背景" |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726250"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
獲取可能支援此物件表示的屬性的欄位或變數(如果有)。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>參數
`ppObject`\
[出]描述備份欄位的[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件表示託管代碼類屬性,即具有 get 和/或設置訪問器的方法。 此類屬性通常需要變數來包含屬性操作的值。 此變數稱為後備欄位。 如果物件沒有支援欄位,請確保返回 null 值:某些呼叫方可能不會注意返回值,而是查看是否`ppObject`在中傳回了 null 值。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
