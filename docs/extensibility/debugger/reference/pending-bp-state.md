---
title: PENDING_BP_STATE |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae632ab67a21d795a0594d37301c162c1c4ba753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125912"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
指定的暫止中斷點 （具有尚未已繫結中斷點） 的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>成員  
 PBPS_NONE  
 零的的預留位置。 絕對不會傳回此值。  
  
 PBPS_DELETED  
 表示已刪除暫止中斷點。  
  
 PBPS_DISABLED  
 表示暫止中斷點已停用。  
  
 PBPS_ENABLED  
 指出已啟用 暫止中斷點。  
  
## <a name="remarks"></a>備註  
 使用做為`state`隸屬[PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)