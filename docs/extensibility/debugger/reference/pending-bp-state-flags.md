---
title: "PENDING_BP_STATE_FLAGS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE_FLAGS
helpviewer_keywords: PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c89469cd1b2d41fc0e3258d2875b9e22b7c55747
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
指定的暫止中斷點的狀態旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## <a name="members"></a>成員  
 PBPSF_NONE  
 預留位置。  
  
 PBPSF_VIRTUALIZED  
 指定虛擬化暫止中斷點，每次載入新的程式碼時要繫結的其中一個。  
  
## <a name="remarks"></a>備註  
 用於`flags`隸屬[PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)