---
title: IDebugGenericParamField::GetFlags |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51aed81c26a4f62185d3dd7bcd588b7e955a92d9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934336"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
擷取此泛型參數的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```csharp  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwFlags`  
 [out]傳回此泛型參數的旗標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這些旗標包含各種特殊條件約束的相關資訊。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CDebugGenericParamFieldType**公開 （expose） 的物件[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面。  
  
```cpp  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)