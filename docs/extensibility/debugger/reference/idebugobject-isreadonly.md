---
title: IDebugObject::IsReadOnly | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 13ede24192408b7b5a68c13d37a4535ccf352fed
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Determines if this object is read-only.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pfIsReadOnly`  
 [out] Returns non-zero (`TRUE`) if this object is read-only; otherwise, returns zero (`FALSE`).  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 A read-only object cannot have its value changed after it is created.  
  
## <a name="see-also"></a>See Also  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
