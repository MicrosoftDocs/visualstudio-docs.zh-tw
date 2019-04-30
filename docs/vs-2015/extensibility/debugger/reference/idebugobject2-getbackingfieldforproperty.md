---
title: IDebugObject2::GetBackingFieldForProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536382"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
取得變數的欄位 （如果有的話），可能會支援這個物件所表示的屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

#### <a name="parameters"></a>參數
 `ppObject`

 [out][IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件，描述支援欄位。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)物件代表 managed 程式碼類別屬性，也就是使用 get 方法和 （或) set 存取子。 這類屬性通常會需要一個變數能夠容納操作屬性的值。 這個變數就是所謂的支援欄位。 如果物件不支援欄位，請務必傳回 null 值： 有些呼叫端可能會不注意傳回的值，但將會改為查看中已傳回了 null 值`ppObject`。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)