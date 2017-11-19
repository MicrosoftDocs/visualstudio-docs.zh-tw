---
title: "THREADSTATE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADSTATE
helpviewer_keywords: THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 495425e8a91d42d1da4c3a36f7e3be1e02031329
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="threadstate"></a>THREADSTATE
指定執行緒的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
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
 指出已凍結執行緒 （可以執行不會執行）。  
  
## <a name="remarks"></a>備註  
 用於`dwThreadState`欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)