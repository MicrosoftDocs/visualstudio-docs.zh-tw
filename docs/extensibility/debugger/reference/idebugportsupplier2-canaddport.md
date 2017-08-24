---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 6b9e9de90ec43cbbb7a284dc3e79f14fbd87fbc9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Verifies that a port supplier can add new ports.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```cs  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Return Value  
 If the port can be added, returns `S_OK`; otherwise, returns `S_FALSE` to indicate no ports can be added to this port supplier.  
  
## <a name="remarks"></a>Remarks  
 Call this method before calling the [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) method since the latter method creates the port as well as adding it, which could be a time-consuming operation.  
  
## <a name="see-also"></a>See Also  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
