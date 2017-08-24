---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: e656313cdd0ffce45e7e2668990db1e22bf0f5f9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Gets an enumerator of all elements of the array.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```cs  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppEnum`  
 [out] Returns an [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) object that allows enumerating over all elements.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 As an alternative, use the [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) and [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) methods to iterate through the elements.  
  
## <a name="see-also"></a>See Also  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
