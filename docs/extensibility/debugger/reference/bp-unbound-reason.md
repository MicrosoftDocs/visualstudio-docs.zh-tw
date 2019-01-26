---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d8dfc8e032eecc854a0572c8a7bd14b0c551df7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028617"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
提供中斷點已繫結的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
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
 包含中斷點的程式碼已卸載。  
  
 BPUR_BREAKPOINT_REBIND  
 中斷點具有已重新繫結至不同的位置中。 這可以在下班之後編輯並繼續作業時的中斷點會移動，或當中斷點繫結至已不再有效的路徑與檔案。  
  
 BPUR_ BREAKPOINT_ERROR  
 中斷點會判斷它繫結之後會發生錯誤。 這是受管理的條件不再是有效的中斷點。  
  
## <a name="remarks"></a>備註  
 所傳回[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)