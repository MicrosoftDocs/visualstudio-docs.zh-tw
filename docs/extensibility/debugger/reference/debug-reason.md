---
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6102c0897c80fc927713d2f8bb1e5c83708e6bd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000194"
---
# <a name="debugreason"></a>DEBUG_REASON
指定處理序已啟動偵錯，原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>參數  
 DEBUG_REASON_ERROR  
 發生非特定的錯誤 （這用做預設條件時沒有其他理由調整）。  
  
 DEBUG_REASON_USER_LAUNCHED  
 在使用者的要求啟動程序。  
  
 DEBUG_REASON_USER_ATTACHED  
 已在執行程序已附加至使用者。  
  
 DEBUG_REASON_AUTO_ATTACHED  
 此程序已自動附加至其啟動時。  
  
 DEBUG_REASON_CAUSALITY  
 處理序已啟動，因為*Just In Time* (JIT) 偵錯事件。  
  
## <a name="remarks"></a>備註  
 傳回從[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)