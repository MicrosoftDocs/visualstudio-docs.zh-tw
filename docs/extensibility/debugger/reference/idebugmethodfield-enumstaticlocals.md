---
title: IDebugMethodField：： EnumStaticLocals |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727149"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
建立方法之靜態區域變數的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>參數
`ppLocals`\
擴展傳回代表靜態區域變數清單的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件。 如果沒有靜態區域變數，則會傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，或如果沒有靜態區域變數，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 每個元素都是代表不同靜態區域變數類型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。 在每個物件上呼叫 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 方法，以判斷該物件所代表的靜態區域變數種類。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
