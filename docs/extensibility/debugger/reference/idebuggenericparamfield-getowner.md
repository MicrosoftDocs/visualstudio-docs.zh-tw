---
title: IDebugGenericParamField::獲取擁有者 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetOwner
ms.assetid: c7f6d166-a69e-40c4-bd0b-1a1fdf9aaacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 040b8cf21cda1a0634c1c423516109b1ef214f01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727868"
---
# <a name="idebuggenericparamfieldgetowner"></a>IDebugGenericParamField::GetOwner
檢索此泛型參數的類型或方法擁有者。

## <a name="syntax"></a>語法

```cpp
HRESULT GetOwner(
    IDebugField** ppOwner
);
```

```csharp
int GetOwner(
    out IDebugField ppOwner
);
```

## <a name="parameters"></a>參數
`ppOwner`\
[出]返回擁有此泛型參數的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面的**CDebugGenericParamFieldType**物件實現此方法。

```cpp
HRESULT CDebugGenericParamFieldType::GetOwner(IDebugField** ppOwner)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetOwner );

    IfFalseGo(ppOwner, E_INVALIDARG );
    *ppOwner = NULL;

    IfFailGo( this->LoadProps() );
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );

    switch (TypeFromToken(m_tokOwner))
    {
        case mdtMethodDef:
            {
                mdTypeDef tokClass;
                CComPtr<IDebugField> pClass;
                CDEBUG_ADDRESS caddr;
                CComPtr<IDebugContainerField> pContainer;

                IfFailGo( pMetadata->GetMethodProps( m_tokOwner, &tokClass, NULL, 0, NULL, NULL, NULL, NULL, NULL, NULL ) );
                IfFailGo( m_spSH->CreateClassType(m_idModule, tokClass, &pClass) );
                IfFailGo( pClass->QueryInterface( &pContainer ) );
                IfFailGo( caddr.InitializeMethod( m_idModule, tokClass, m_tokOwner, 0, 0 ) );
                IfFailGo( m_spSH->CreateMethodSymbol( pContainer, caddr, FIELD_SYM_MEMBER, ppOwner ) );
                break;
            }
        case mdtTypeDef:
            {
                IfFailGo( m_spSH->CreateClassType(m_idModule, m_tokOwner, ppOwner) );
                break;
            }
        default:
            {
                ASSERT(!"Unexpected Owner type for Generic Param Field");
                hr = E_FAIL;
            }
    }
Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetOwner, hr );
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
