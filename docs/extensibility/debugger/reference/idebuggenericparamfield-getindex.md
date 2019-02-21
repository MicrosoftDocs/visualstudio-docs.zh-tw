---
title: IDebugGenericParamField::GetIndex | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77fe5e06562292eaef477b77d05f685c7c1f9d35
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450187"
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
擷取此泛型參數的索引。

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

#### <a name="parameters"></a>參數
`pIndex`  
[out]此泛型參數的索引值。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
例如，對於 Dictionary(K,V)，K 是索引為 0，V 索引 1。

## <a name="example"></a>範例
下列範例示範如何實作這個方法，如**CDebugGenericParamFieldType**公開 （expose） 的物件[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面。

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
[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
