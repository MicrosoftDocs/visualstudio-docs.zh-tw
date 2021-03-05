---
description: 從連續的位元組序列設定物件的值。
title: IDebugObject：： SetValue |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 972281335b964679f38693182e42c4e64074dffa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167148"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
從連續的位元組序列設定物件的值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>參數
`pValue`\
在表示新值的位元組陣列。

`nSize`\
在值的大小（以位元組為單位）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 陣列中的值會複製到這個 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件，並取代任何現有的值。 新值的大小可以大於或小於現有的值。 這 `IDebugObject` 不能是 null 參考。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
