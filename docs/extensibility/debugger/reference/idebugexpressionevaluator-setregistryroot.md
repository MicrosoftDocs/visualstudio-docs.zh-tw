---
title: IDebugExpressionEvaluator：： SetRegistryRoot |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11e7cd69ed3f1e1b23cc0f2f03f3fd2cf912d308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729423"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
這個方法會設定登錄根目錄。 用於並存的偵錯工具。

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
在新的登錄根目錄。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 指定的登錄根目錄通常是在運算式評估工具第一次具現化時設定，並指向特定 Visual Studio 版本 (HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. y*的登錄機碼，其中*X. y*是) 的版本號碼。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
