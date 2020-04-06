---
title: IDebugModule2::獲取資訊 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726957"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
獲取有關此模塊的資訊。

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
[在][MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)枚舉中的標誌的組合,用於指定要填寫`pInfo`的 欄位。

`pInfo`\
[進出]填充模塊說明的[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構包含模組**視窗**中顯示的模組的名稱。

## <a name="see-also"></a>另請參閱
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
