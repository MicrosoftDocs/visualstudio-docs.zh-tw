---
description: 取得服務物件的唯一識別碼。
title: IDebugExpressionEvaluator2：： GetService |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092003"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
取得服務物件的唯一識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>參數
`uid`\
在要抓取之服務的唯一識別碼。

`ppService`\
擴展傳回代表服務的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這可由協力廠商運算式評估工具取用，以從另一個運算式評估工具取得服務。 例如，這個方法可用來從預設運算式評估工具取得視覺化程式服務的介面。 協力廠商運算式評估工具不太可能需要執行這個介面。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
