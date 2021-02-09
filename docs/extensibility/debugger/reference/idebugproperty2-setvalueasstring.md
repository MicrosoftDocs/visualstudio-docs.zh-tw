---
title: IDebugProperty2：： SetValueAsString |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 812bb7807a8b739d09cb15c6f03e58732fde20a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916034"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
從指定的字串設定屬性的值。

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
在字串，包含要設定的值。

`nRadix`\
在用來解讀任何數值資訊的基數。 這可以是0，以嘗試自動判斷基數。

`dwTimeout`\
在指定從這個方法傳回之前等候的最長時間（以毫秒為單位）。 使用 `INFINITE` 可無限期等候。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 下表顯示其他可能的值。

|值|描述|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|無法將字串轉換成屬性值，或無法設定屬性值。|
|`E_SETVALUE_VALUE_IS_READONLY`|此為唯讀屬性。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
