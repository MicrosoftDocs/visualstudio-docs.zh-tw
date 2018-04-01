---
title: IDebugGenericParamField::GetIndex |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 859764a8673c953e3a2dffa06219349e8f76db6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
擷取這個泛型參數的索引。  
  
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
 [out]這個泛型參數的索引值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 例如，對於 Dictionary(K,V)，K 是索引 0，V 索引 1。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來**CDebugGenericParamFieldType**公開物件[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)介面。  
  
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
  
## <a name="see-also"></a>請參閱  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)