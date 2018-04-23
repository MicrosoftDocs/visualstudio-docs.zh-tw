---
title: BP_FLAGS90 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f8153f3fb2419e26f7e7d3a741ae4c79c9272a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="bpflags90"></a>BP_FLAGS90
列舉有效的選擇性旗標值。 選擇性旗標可能會用來指定當您設定中斷點的其他資訊。 這個列舉型別擴充[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)列舉型別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>參數  
 BP90_FLAG_NONE  
 不指定任何中斷點旗標。  
  
 BP90_FLAG_MAP_DOCPOSITION  
 指定應使用的文件位置將中斷點對應的偵錯引擎 (DE)。 這是僅適用於指令碼為導向的來源檔案，例如 Active Server Pages (ASP) 中設定中斷點。  
  
 BP90_FLAG_DONT_STOP  
 指定應該處理由偵錯引擎的中斷點，但是，偵錯引擎最後應該不會阻止那里;也就是說， [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)不應傳送事件的物件。 這個旗標被設計主要是用於追蹤點。  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 若要判斷是否應該清除逐步執行的狀態使用的原生偵錯引擎。 它與不同 BP90_FLAG_DONT_STOP 因為 BP90_FLAG_DONT_STOP 未設定追蹤點執行巨集。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg90.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)