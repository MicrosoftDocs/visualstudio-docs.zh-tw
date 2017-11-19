---
title: "BP_PASSCOUNT |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_PASSCOUNT
helpviewer_keywords: BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45fdea434b419f0e681e8946c4c8dee3db945d8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="bppasscount"></a>BP_PASSCOUNT
描述引發的條件式中斷點的計數和條件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>成員  
 `dwPassCount`  
 引發它之前通過中斷點次數。  
  
 `stylePassCount`  
 中的值[BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)列舉，指定之中斷點的樣式傳遞計數。  
  
## <a name="remarks"></a>備註  
 這個結構是屬於[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構。  
  
 此結構也會當做參數傳遞[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)和[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)