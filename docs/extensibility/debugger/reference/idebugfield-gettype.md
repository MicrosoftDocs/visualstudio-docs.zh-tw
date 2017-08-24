---
title: IDebugField::GetType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 6f2c8564fc2397743b31ad92f2d1517c16848696
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
This method gets the type of field.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```cs  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppType`  
 [out] Returns the field type as another [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) object.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="see-also"></a>See Also  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
