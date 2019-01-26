---
title: PENDING_BP_STATE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db6f2b84c0d10ed6be171ad1c3055ca8f02fa5db
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958156"
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
指定暫止中斷點的狀態旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## <a name="members"></a>成員  
 PBPSF_NONE  
 預留位置。  
  
 PBPSF_VIRTUALIZED  
 指定虛擬化暫止中斷點，另一個則是每次載入新的程式碼時，繫結。  
  
## <a name="remarks"></a>備註  
 用於`flags`隸屬[PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)