---
title: IDebugPropertyField::GetPropertyGetter |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c1a9f712555de6f4b8400f828bf18aca13c779d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164891"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得取得屬性的方法。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp#  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppField`  
 [out]傳回[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件，表示取得屬性的方法。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要取得設定屬性，此方法[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)呼叫方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
