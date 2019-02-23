---
title: IDebugObject2::GetField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetField
helpviewer_keywords:
- IDebugObject2::GetField method
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 797a18b678e815411b7ea7860e44ea6159caa2b5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708195"
---
# <a name="idebugobject2getfield"></a>IDebugObject2::GetField
取得這個物件的型別。

## <a name="syntax"></a>語法

```cpp
HRESULT GetField(
 IDebugField** ppField
);
```

```csharp
int GetField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>參數
 `ppField`

 [out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件如果不是 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 欄位描述的物件型別。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)