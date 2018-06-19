---
title: BP_FLAGS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 481dd21287ba3ca68c2abc61412785fc0151788d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109947"
---
# <a name="bpflags"></a>BP_FLAGS
提供可用來設定中斷點時指定的其他資訊的選擇性旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>成員  
 BP_FLAG_NONE  
 不指定任何中斷點旗標。  
  
 BP_FLAG_MAP_DOCPOSITION  
 指定偵錯引擎 (DE) 應該對應使用文件位置中斷點。 這是僅適用於指令碼為導向的來源檔案，例如 Active Server Pages (ASP) 中設定中斷點。  
  
 BP_FLAG_DONT_STOP  
 指定應該處理由偵錯引擎的中斷點，但是，偵錯引擎最後應該不會阻止那里 (也就是[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)不應傳送事件的物件)。 這個旗標被設計主要是用於追蹤點。  
  
## <a name="remarks"></a>備註  
 用於`dwFlags`隸屬[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
 這些值可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)