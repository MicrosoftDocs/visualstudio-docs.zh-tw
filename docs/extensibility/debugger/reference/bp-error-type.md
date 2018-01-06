---
title: "BP_ERROR_TYPE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_ERROR_TYPE
helpviewer_keywords: BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c50e5cb9f9ba1edf09a30b13373a680ff8e5a3f2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
指定中斷點之錯誤型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 BPET_NONE  
 不指定任何中斷點錯誤。  
  
 BPET_TYPE_WARNING  
 指定警告樣式中斷點錯誤。  
  
 BPET_TYPE_ERROR  
 指定中斷點 error 類型錯誤。  
  
 BPET_SEV_HIGH  
 指定高嚴重性中斷點錯誤。  
  
 BPET_SEV_GENERAL  
 指定媒體嚴重性中斷點錯誤。  
  
 BPET_SEV_LOW  
 指定的低嚴重性中斷點錯誤。  
  
 BPET_TYPE_MASK  
 指定遮罩樣式中斷點錯誤。  
  
 BPET_SEV_MASK  
 指定的嚴重性遮罩樣式中斷點錯誤。  
  
 BPET_GENERAL_WARNING  
 指定的一般警告樣式中斷點錯誤。  
  
 BPET_GENERAL_ERROR  
 指定中斷點一般 error 類型錯誤。  
  
 BPET_ALL  
 指定中斷點的所有錯誤類型。  
  
## <a name="remarks"></a>備註  
 這些值可能會合併使用位元`OR`和用於`dwType`隸屬[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構。 做為參數來傳遞[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)方法。  
  
 中斷點錯誤類型被組成類型和嚴重性。 這表示中斷點錯誤類型永遠不會是型別 (例如， `BPET_TYPE_ERROR`，) 或嚴重性 (例如， `BPET_SEV_GENERAL`) 本身。 `BPET_GENERAL_WARNING`和`BPET_GENERAL_ERROR`一般警告和錯誤的中斷點提供預先定義的值。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)