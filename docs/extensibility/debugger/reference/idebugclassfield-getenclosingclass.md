---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
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
ms.openlocfilehash: 78e3e0a201c2cfa7ecc68828def8793c0ade34cd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Gets the class that encloses this class.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```cs  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppClassField`  
 [out] Returns an [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) object representing the enclosing class. Returns a null value if there is no enclosing class.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 If the class represented by this [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) object is a nested class, then the `ppClassField` parameter returns an `IDebugClassField` object representing the enclosing class. For example, given this class definition:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Calling the `GetEnclosingClass` method on the `IDebugClassField` object representing the `NestedClass` class returns an `IDebugClassField` object representing the class `RootClass`.  
  
## <a name="see-also"></a>See Also  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
