---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
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
ms.openlocfilehash: 9c61891876f3e27753283042b0b24dd7d7d60dfd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
This method determines whether the port supplier can persist ports (by writing them to disk) between invocations of the debugger.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parameters  
 None.  
  
## <a name="return-value"></a>Return Value  
 `S_OK` if ports can be persisted, or `S_FALSE` to indicate that ports cannot be persisted.  
  
## <a name="remarks"></a>Remarks  
 If the port supplier can persist ports, it should do so when it is destroyed and then reload them when it is instantiated once again.  
  
## <a name="see-also"></a>See Also  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
