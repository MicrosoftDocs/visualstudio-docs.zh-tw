---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
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
ms.openlocfilehash: c9441dc96ca5c090f246d4b27842afa6270e1ffb
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
This method gets the machine utilities for a server.  
  
> [!NOTE]
>  This method is obsolete: do not use ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] always returns `E_NOTIMPL` if this method is called). It is retained for historical reasons.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppUtil`  
 [out] Returns an `IDebugMDMUtil2_V7` interface that represents the machine utilities information.  
  
## <a name="return-value"></a>Return Value  
 Always returns `E_NOTIMPL`, indicating that the method is not implemented.  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] always returns `E_NOTIMPL` if this method is called.  
  
## <a name="see-also"></a>See Also  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
