---
title: DEBUG_REASON |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47cfd171d23420396c6d7ab5416db32cc05511f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="debugreason"></a>DEBUG_REASON
指定處理程序已啟動偵錯的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>參數  
 DEBUG_REASON_ERROR  
 發生非特定的錯誤 （這用做為預設值條件時沒有其他的理由，調整）。  
  
 DEBUG_REASON_USER_LAUNCHED  
 在使用者的要求已啟動的處理序。  
  
 DEBUG_REASON_USER_ATTACHED  
 已執行的處理序已附加至使用者。  
  
 DEBUG_REASON_AUTO_ATTACHED  
 處理序已自動附加至其啟動時。  
  
 DEBUG_REASON_CAUSALITY  
 由於已啟動的處理程序*時間恰好*(JIT) 偵錯事件。  
  
## <a name="remarks"></a>備註  
 傳回從[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)