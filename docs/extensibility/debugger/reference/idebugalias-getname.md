---
description: 取得此別名的名稱。
title: IDebugAlias：： GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51deb460e5ce30bfea076af9a1f0c1efd2df9673
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059154"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
取得此別名的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName(
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>參數
`pbstrName`\
擴展別名的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
