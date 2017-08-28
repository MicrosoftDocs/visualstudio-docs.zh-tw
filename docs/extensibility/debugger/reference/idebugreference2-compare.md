---
title: IDebugReference2::Compare | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 287e9f4e4266f9e76812c605376875e12bea9c7b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Compares one reference to another. Reserved for future use.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Compare (   
   REFERENCE_COMPARE dwCompare,  
   IDebugReference2* pReference  
);  
```  
  
```csharp  
int Compare (   
   enum_REFERENCE_COMPARE dwCompare,  
   IDebugReference2       pReference  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dwCompare`  
 [in] A value from the [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) enumeration that specifies the comparison operation, for example, equal to, less than, or greater than.  
  
 `pReference`  
 [in] An [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) object representing the reference to be compared to.  
  
## <a name="return-value"></a>Return Value  
 Always returns `E_NOTIMPL`.  
  
## <a name="see-also"></a>See Also  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
