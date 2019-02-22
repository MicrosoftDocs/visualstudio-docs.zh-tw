---
title: THREADSTATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8acfff2f3b37cfe44565a432ff150073b3ab07ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962140"
---
# <a name="threadstate"></a>THREADSTATE
指定執行緒的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>成員  
 THREADSTATE_RUNNING  
 表示執行緒正在執行。  
  
 THREADSTATE_STOPPED  
 表示執行緒已停止因為中斷點。  
  
 THREADSTATE_FRESH  
 表示執行緒已建立，但尚未執行的程式碼。  
  
 THREADSTATE_DEAD  
 表示執行緒已無作用。  
  
 THREADSTATE_FROZEN  
 表示已凍結執行緒 （可以執行任何執行）。  
  
## <a name="remarks"></a>備註  
 用於`dwThreadState`欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)