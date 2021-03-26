---
description: 這個方法會傳回代表列舉名稱的 IDebugField。
title: IDebugEnumField：： GetUnderlyingSymbol |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9343c1b0908c6b132ea982a46623b8c1cf20efc9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092562"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
這個方法會傳回代表列舉名稱的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。

## <a name="syntax"></a>語法

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
擴展傳回描述此列舉名稱的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的名稱也包含列舉的型別，此型別會使用 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)系結至記憶體位置。

## <a name="see-also"></a>另請參閱
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
