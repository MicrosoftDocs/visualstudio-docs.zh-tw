---
title: IDebugPropertyField::GetPropertySetter |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8484aa4041e00b9decce73dc9e19e22aa106e9df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164855"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得設定屬性的方法。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```csharp  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppField`  
 [out]傳回[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件，表示設定屬性的方法。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 若要取得之屬性的方法，呼叫[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
