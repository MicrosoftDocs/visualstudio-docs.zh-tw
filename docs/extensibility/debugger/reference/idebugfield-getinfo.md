---
title: IDebugField：： GetInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21d80f222bdea8a8e17a9b74eefb7885cab0c289
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869904"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
這個方法會取得欄位的可顯示資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>參數
`dwFields`\
在 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 常數的組合，可選取要顯示的資訊。 如果欄位代表符號，這通常是符號名稱和類型。

`pFieldInfo`\
擴展傳回所提供之 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 結構中的資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
