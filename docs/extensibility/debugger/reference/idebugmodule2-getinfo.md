---
description: 取得此模組的相關資訊。
title: IDebugModule2：： GetInfo |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a31c6e40f18e3b405449179e3e5a3ea1a42acc6f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150559"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
取得此模組的相關資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>參數
`dwFields`\
在 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 列舉中的旗標組合，可指定 `pInfo` 要填寫的欄位。

`pInfo`\
[in，out]填入模組描述的 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構包含 [**模組**] 視窗中顯示的模組名稱。

## <a name="see-also"></a>另請參閱
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
