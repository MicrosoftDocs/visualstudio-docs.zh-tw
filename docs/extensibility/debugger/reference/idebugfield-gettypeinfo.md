---
description: 這個方法會取得與符號或類型無關的類型相關資訊。
title: IDebugField：： GetTypeInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ea120cb58faa28bbb8168800ef6e35f707d879f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073699"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
這個方法會取得與符號或類型無關的類型相關資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>參數
`pTypeInfo`\
擴展傳回所提供之 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 結構中的型別資訊。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 與型別無關的資訊會包括 AppDomain、模組，以及包含符號的類別。

## <a name="see-also"></a>另請參閱
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
