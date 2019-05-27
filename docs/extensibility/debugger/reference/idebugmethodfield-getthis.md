---
title: IDebugMethodField::GetThis |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3e88f209b506d8baf10a779d282a78122c274fb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211930"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
取得`this`(`Me`在[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) 的物件，包含方法的指標。

## <a name="syntax"></a>語法

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>參數
`ppClass`\
[out]傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件，代表"this"指標。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 在物件導向語言中，有通常是目前的具現化之類別的隱含的指標。 這就所謂`this`在C#/C++和 as`Me`中[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)