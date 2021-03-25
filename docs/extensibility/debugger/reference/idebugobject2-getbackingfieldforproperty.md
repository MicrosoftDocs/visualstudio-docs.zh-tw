---
description: 取得欄位或變數 (是否有任何可支援此物件所表示之屬性的) 。
title: IDebugObject2：： GetBackingFieldForProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 210381e034ccae8ab9662b77c47970af2affa095
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053798"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
取得欄位或變數 (是否有任何可支援此物件所表示之屬性的) 。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>參數
`ppObject`\
擴展描述支援欄位的 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件代表 managed 程式碼類別屬性，也就是具有 get 和/或 set 存取子的方法。 這類屬性通常需要變數以包含屬性所操作的值。 此變數稱為支援欄位。 如果物件沒有支援欄位，則請務必傳回 null 值：某些呼叫端可能不會注意傳回值，而是會查看是否已在中傳回 null 值 `ppObject` 。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
