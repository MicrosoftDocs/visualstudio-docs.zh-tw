---
title: IDebugGenericField實例::獲取類型參數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c41a3f314f641ed4bff116959b6d70f0a5fb9dcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728188"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
檢索此實例的類型參數參數參數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypeArguments(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   ULONG32*      pcArgs
);
```

```csharp
int GetTypeArguments(
   uint              cArgs,
   out IDebugField[] ppArgs,
   ref uint          pcArgs
);
```

## <a name="parameters"></a>參數
`cArgs`\
[在]類型參數數。

`ppArgs`\
[出]返回類型參數陣組。

`pcArgs`\
[進出]`ppArgs`陣列中的成員數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)
