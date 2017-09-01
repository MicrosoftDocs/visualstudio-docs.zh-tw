---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
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
ms.openlocfilehash: 2afb0101aac51709439141109ffe2348f72142b0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Returns a structure describing an object and its location within its scope or container.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pAddress`  
 [in, out] A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure that is filled in by this method.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure is passed to this method, which then fills it in with the appropriate information. How this information is interpreted depends on the kind of information returned and the symbol handler itself. See [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) for more details.  
  
## <a name="see-also"></a>See Also  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
