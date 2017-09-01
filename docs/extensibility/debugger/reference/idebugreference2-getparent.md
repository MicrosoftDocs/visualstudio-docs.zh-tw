---
title: IDebugReference2::GetParent | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
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
ms.openlocfilehash: 6ad3a164eb6a214d0fa35cface5d157567d52eb7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Gets the parent reference of a reference. Reserved for future use.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppParent`  
 [out] Returns an [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) object that represents the parent of this property.  
  
## <a name="return-value"></a>Return Value  
 Always returns `E_NOTIMPL`.  
  
## <a name="see-also"></a>See Also  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
