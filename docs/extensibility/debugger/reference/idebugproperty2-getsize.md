---
title: IDebugProperty2::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
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
ms.openlocfilehash: 00674430f95eed895a6564676e9d33a36795268d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Gets the size, in bytes, of the property value.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pdwSize`  
 [out] Returns the size, in bytes, of the property value.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise returns error code. Returns `S_GETSIZE_NO_SIZE` if the property has no size.  
  
## <a name="see-also"></a>See Also  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
