---
title: IDebugField::GetAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
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
ms.openlocfilehash: 56cf317fad706249ef88be6dc6e0fea470b874eb
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
This method gets the debug address of a field.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppAddress`  
 [out] Returns the address as an [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) object.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, return an error code.  
  
## <a name="see-also"></a>See Also  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
