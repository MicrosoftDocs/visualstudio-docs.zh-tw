---
description: 這個方法會傳回與這個物件相關聯的引數類型數目。
title: IDebugBinder3：： GetTypeArgumentCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa70a07273a0b4dfdf24219949b411f42b0ddc44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054487"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
這個方法會傳回與這個物件相關聯的引數類型數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypeArgumentCount(
   UINT* uCount
);
```

```csharp
int GetTypeArgumentCount(
   out uint uCount
);
```

## <a name="parameters"></a>參數
`uCount`\
擴展與這個物件相關聯的引數類型數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的值可以用來配置陣列，以與 [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) 方法搭配使用。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)
