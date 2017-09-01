---
title: IDebugExtendedField::IsClosedType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 8
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
ms.openlocfilehash: f211ba7bebcc0dc87ef1ffd3905d3526203fc08c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Determines if the field represents a closed type.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Return Value  
 If the field is a closed type, returns `S_OK`; otherwise, returns `S_FALSE`.  
  
## <a name="see-also"></a>See Also  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
