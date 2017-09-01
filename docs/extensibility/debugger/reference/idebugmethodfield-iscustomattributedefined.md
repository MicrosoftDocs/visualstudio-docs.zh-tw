---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
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
ms.openlocfilehash: 95a6058a5e63b4d43600bff7e567b91a1dbd964d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Determines whether a specific custom attribute has been defined.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pszCustomAttributeName`  
 [in] A string containing the name of the custom attribute to find.  
  
## <a name="return-value"></a>Return Value  
 Returns S_OK if the custom attribute is defined on this method, otherwise returns S_FALSE.  
  
## <a name="see-also"></a>See Also  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
