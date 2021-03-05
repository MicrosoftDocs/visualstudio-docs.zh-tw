---
description: 抓取評估內容的名稱。
title: IDebugExpressionCoNtext2：： GetName |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d43af7eeb733aca978a4c3b09fd4f97ca828fe5a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152645"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
抓取評估內容的名稱。

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
擴展傳回評估內容的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 名稱是此評估內容的描述。 它通常可以由參考此確切評估內容的運算式評估工具剖析。 例如，在 c + + 中，名稱如下所示：

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>另請參閱
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
