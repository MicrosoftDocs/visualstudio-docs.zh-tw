---
title: "BP_FLAGS90 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e958be77ca266af30556fa8c03c580eea94b903
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

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
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
