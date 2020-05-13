---
title: IDebug屬性2::設置價值字串 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721235"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
設置給定字串中屬性的值。

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
[在]包含要設定的值的字串。

`nRadix`\
[在]用於解釋任何數值資訊的半徑。 這可以是 0,以嘗試自動確定半徑。

`dwTimeout`\
[在]指定從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。 下表顯示了其他可能的值。

|值|描述|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|無法將字串轉換為屬性值,或者無法設置屬性值。|
|`E_SETVALUE_VALUE_IS_READONLY`|此為唯讀屬性。|

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
