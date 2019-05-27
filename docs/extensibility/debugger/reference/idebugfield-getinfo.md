---
title: IDebugField::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d28db6824afe6230cc8e00fae8e144dc541af59
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212200"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
這個方法會取得可顯示的欄位資訊。

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
[in]組合[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)常數，以選取要顯示的資訊。 如果欄位代表符號，這通常是符號名稱和型別。

`pFieldInfo`\
[out]傳回所提供的資訊[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)