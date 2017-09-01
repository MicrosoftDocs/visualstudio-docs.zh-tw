---
title: IDebugBinder::GetFunctionObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: 11
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
ms.openlocfilehash: 140175a74c8999787cea0aa0940e7ec5201695aa
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
This method gets an [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) object used to create function parameters.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppFunction`  
 [out] Returns the [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface that is used to create function parameters.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="see-also"></a>See Also  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
