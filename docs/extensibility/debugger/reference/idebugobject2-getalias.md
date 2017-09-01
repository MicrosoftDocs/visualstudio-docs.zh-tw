---
title: IDebugObject2::GetAlias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: 7
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3dea81100ee3b6d8a7ee8f1024f87784aadbe181
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Gets the alias associated with this object, if any.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppAlias`  
 [out] Returns an [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) object representing the alias for this object; otherwise, returns a null value.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 An alias for an object is created with a call to the [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) method.  
  
## <a name="see-also"></a>See Also  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
