---
title: IDebugField::Equal | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
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
ms.openlocfilehash: 759043a8cd324ad393893474752beaa8615dbb62
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugfieldequal"></a>IDebugField::Equal
This method compares this field with the specified field for equality.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pField`  
 [in] The field to compare to this one.  
  
## <a name="return-value"></a>Return Value  
 If the fields are the same, returns `S_OK`. If the fields are different, returns `S_FALSE.` Otherwise, returns an error code.  
  
## <a name="see-also"></a>See Also  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
