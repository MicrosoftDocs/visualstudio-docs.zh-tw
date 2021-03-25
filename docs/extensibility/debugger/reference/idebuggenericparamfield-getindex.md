---
description: 抓取這個泛型參數的索引。
title: IDebugGenericParamField：： GetIndex |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 210a66db89998cff2cde043ceb1c1cf21f23d8ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073478"
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
抓取這個泛型參數的索引。

## <a name="syntax"></a>語法

```cpp
HRESULT GetIndex(
    DWORD* pIndex
);
```

```csharp
int GetIndex(
    out uint pIndex
);
```

## <a name="parameters"></a>參數
`pIndex`\
擴展此泛型參數的索引值。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
例如，針對 Dictionary (K，V) ，K 為索引0，V 為索引1。

## <a name="example"></a>範例
下列範例示範如何針對公開 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面的 **CDebugGenericParamFieldType** 物件，執行這個方法。

```cpp
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );

    IfFalseGo(pIndex, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pIndex = m_index;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
