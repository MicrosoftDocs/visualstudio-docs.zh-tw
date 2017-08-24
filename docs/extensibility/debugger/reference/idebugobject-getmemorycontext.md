---
title: IDebugObject::GetMemoryContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
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
ms.openlocfilehash: 72f8df717961d782b6479c48315a841efcbe2bd2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Gets the memory context that represents the address of the value of the object.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```cs  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pContext`  
 [out] Returns an [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) object representing the address of the value of the object.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The returned memory context specifies the address of the value as represented by this [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) object.  
  
## <a name="see-also"></a>See Also  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
