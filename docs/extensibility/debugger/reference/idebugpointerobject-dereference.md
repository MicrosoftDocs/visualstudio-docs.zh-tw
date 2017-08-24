---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
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
ms.openlocfilehash: d86b9e1f8352ff827bf6cc6919c048c60f17e890
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Gets the object pointed to.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```cs  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dwIndex`  
 [in] A simple byte offset from the beginning of the object pointed to.  
  
 `ppObject`  
 [out] Returns an [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) object representing the object pointed to, plus offset, if any.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code. Returns E_FAIL if this object does not point to another object.  
  
## <a name="remarks"></a>Remarks  
 The object pointed to can be a primitive or a more complex type such as a class or structure.  
  
## <a name="see-also"></a>See Also  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
