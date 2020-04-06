---
title: IDebug運算式評估器2::獲取服務 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729358"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
檢索給定其唯一標識符的服務物件。

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
[在]要檢索的服務的唯一標識符。

`ppService`\
[出]返回表示服務的物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 第三方運算式賦值器可以使用這一功能從另一個運算式賦值器獲取服務。 例如,此方法可用於從預設表達式賦值器獲取可視化器服務的介面。 第三方表示式評估器不太可能需要實現此介面。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
