---
title: IDebugCustomAttribute::GetParentField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 158887e9f2d7d7b250b435570d6780e460508816
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921655"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
取得要附加自訂屬性的欄位。

## <a name="syntax"></a>語法

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>參數
 `ppField`

 [out]傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，表示要附加自訂屬性的欄位。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)來判斷什麼種類的欄位的父物件。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)