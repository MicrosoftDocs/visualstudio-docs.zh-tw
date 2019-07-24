---
title: IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2f64272b38b6a41e8637e884f19da62d2fd1a1e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325602"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
這個方法設定的登錄根目錄。 用於並排顯示偵錯。

## <a name="syntax"></a>語法

```cpp
HRESULT SetRegistryRoot ( 
   LPCOLESTR ustrRegistryRoot
);
```

```csharp
int SetRegistryRoot(
   string ustrRegistryRoot
);
```

## <a name="parameters"></a>參數
`ustrRegistryRoot`\
[in]新的登錄根目錄。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 運算式評估工具會先具現化，並點時，通常設定指定的登錄根登錄機碼的 Visual Studio 特定版本 (hkey_local_machine\software\microsoft\visualstudio\\ *X.Y*，其中 *X.Y* 是版本號碼)。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)