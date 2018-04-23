---
title: BP_UNBOUND_REASON |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65398ac0c4bde18dc772d75ceea203bdbfe3b189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
提供中斷點已解除繫結的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>成員  
 BPUR_UNKNOWN  
 未知的原因。  
  
 BPUR_CODE_UNLOADED  
 包含中斷點的程式碼已經卸載。  
  
 BPUR_BREAKPOINT_REBIND  
 中斷點具有已不再重新繫結至不同的位置。 這可以編輯之後，就可能發生，並繼續作業，中斷點就會移，或時的中斷點繫結至已不再有效的路徑與檔案。  
  
 BPUR_ BREAKPOINT_ERROR  
 中斷點會判斷它繫結之後會產生錯誤。 此時若要管理中斷點條件不再有效。  
  
## <a name="remarks"></a>備註  
 所傳回[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)