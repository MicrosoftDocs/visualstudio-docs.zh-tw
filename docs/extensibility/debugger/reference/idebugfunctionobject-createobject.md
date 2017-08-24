---
title: IDebugFunctionObject::CreateObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
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
ms.openlocfilehash: 7887fdec8a5349e3262f69132edf505a92c1ef19
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Creates an object using a constructor.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```cs  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pConstructor`  
 [in] An [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) object representing the constructor of the object to be created.  
  
 `dwArgs`  
 [in] The number of parameters in the `pArg` array. Represents the number of parameters passed to the constructor.  
  
 `pArg`  
 [in] An array of [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objects representing the parameters passed to the constructor.  
  
 `ppObject`  
 [out] Returns an `IDebugObject` representing the newly created object.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Call this method to create an object that represents an instance of a class (or other complex type that requires a constructor) that is a parameter to the function which is represented by the [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
 If the object parameter does not require a constructor, call the [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) method.  
  
## <a name="see-also"></a>See Also  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
