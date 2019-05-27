---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961ac778dab2d17a87748cae8e1210f6b13422d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201053"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
擷取評估內容的名稱。

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
[out]傳回評估內容的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 此評估內容的描述名稱。 它通常是指這個精確的評估內容的運算式評估工具可以剖析的項目。 例如，在C++名稱如下所示：

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>另請參閱
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)