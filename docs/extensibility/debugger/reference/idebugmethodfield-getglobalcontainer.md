---
title: IDebugMethodField::GetGlobalContainer |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40bbee4c00425c4f46ccde35b8a8c810e1d7c8e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872812"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
取得方法的通用的容器。

## <a name="syntax"></a>語法

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

#### <a name="parameters"></a>參數
 `ppClass`

 [out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)代表這個方法會定義模組。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件代表整個模組，而且是假造的物件，也就是模組本身並沒有實際的類別，但它可以由`IDebugClassField`物件，讓各種要列舉和探索到模組的項目。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)