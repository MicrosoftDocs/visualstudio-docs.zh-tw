---
title: IDebugProperty2::SetValueAsString |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27b481165cf95a97d7674d52d8553426dfb6417c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314599"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
從指定的字串中設定屬性的值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>參數
`pszValue`\
[in]字串，包含要設定的值。

`nRadix`\
[in]用於解譯任何數字資訊基數。 這可以是 0，以嘗試自動判斷基數。

`dwTimeout`\
[in]指定的時間上限，以毫秒為單位，從這個方法返回之前等候。 使用`INFINITE`無限期等候。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 下表顯示其他可能的值。

|值|描述|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|字串無法轉換成屬性值，或無法設定屬性值。|
|`E_SETVALUE_VALUE_IS_READONLY`|屬性是唯讀。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)