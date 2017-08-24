---
title: IEnumDebugAddresses::Reset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 5
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
ms.openlocfilehash: 2390ca1e6db27158a72924c62170662a20d758db
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
This method resets the enumeration to the first element.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```cs  
int Reset();  
```  
  
#### <a name="parameters"></a>Parameters  
 None  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 After this method is called, the next call to [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) returns the first element of the enumeration.  
  
## <a name="see-also"></a>See Also  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
