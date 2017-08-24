---
title: IDebugField::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
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
ms.openlocfilehash: 53ae9005d8e20253956e23d978e4472467d4ba36
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
This method gets the size of a field, in bytes.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```cs  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pdwSize`  
 [out] Returns the size.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 All fields have a type and all types have a size. For example, a field with a type of byte has a size of 1 byte.  
  
## <a name="see-also"></a>See Also  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
