---
title: IDebugObject::IsNullReference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
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
ms.openlocfilehash: e43841d4cc991d2fee0631674aac705ddf386b1f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Tests whether this object is a null reference.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```cs  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pfIsNull`  
 [out] Returns non-zero (`TRUE`) if this object is a null reference; otherwise, returns zero (`FALSE`).  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 A null reference means an empty object or an object that has not been assigned to.  
  
## <a name="see-also"></a>See Also  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
