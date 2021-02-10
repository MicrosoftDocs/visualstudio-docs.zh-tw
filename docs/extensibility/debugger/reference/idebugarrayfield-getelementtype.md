---
title: IDebugArrayField：： GetElementType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44b49cbcd52137b31dd456c4cf45bb3fe8ead947
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944643"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
取得陣列中的元素類型。

## <a name="syntax"></a>語法

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>參數
`ppType`\
擴展傳回描述元素類型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)物件會假設陣列的所有元素都是相同的類型。

## <a name="see-also"></a>另請參閱
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
