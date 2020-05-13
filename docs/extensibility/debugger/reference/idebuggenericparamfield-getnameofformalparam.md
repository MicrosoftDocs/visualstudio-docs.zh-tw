---
title: IDebuggenericParamField::獲取正式帕拉姆的名字 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03fb76b96804df900e21b0f91b9c5ba599449cf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727967"
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
檢索此泛型參數的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetNameOfFormalParam (
    BSTR* pbstrName
);
```

```csharp
int GetNameOfFormalParam (
    string pbstrName
);
```

## <a name="parameters"></a>參數
`pbstrName`\
[出]此泛型參數的名稱。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面的**CDebugGenericParamFieldType**物件實現此方法。

```cpp
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)
{
    HRESULT hr = S_OK;
    CComBSTR bstrName;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );

    IfFalseGo( pbstrName, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
