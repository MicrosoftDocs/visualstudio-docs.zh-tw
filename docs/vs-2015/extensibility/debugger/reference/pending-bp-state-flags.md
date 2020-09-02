---
title: PENDING_BP_STATE_FLAGS |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39669e2c1268c2e5d2a294f5b95c314500ead78a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205091"
---
# <a name="pending_bp_state_flags"></a>PENDING_BP_STATE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定暫止的中斷點狀態旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 占 位 符。  
  
 PBPSF_VIRTUALIZED  
 指定虛擬暫止中斷點，這是每次載入新的程式碼時要系結的中斷點。  
  
## <a name="remarks"></a>備註  
 用於 `flags` [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) 結構的成員。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [枚舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
