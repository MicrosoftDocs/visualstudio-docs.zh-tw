---
title: THREADSTATE |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b62e8770449fc71a47d325d933b54b2090f59e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491393"
---
# <a name="threadstate"></a>THREADSTATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[THREADSTATE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/threadstate)。  
  
指定執行緒的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 表示已凍結執行緒 （可以執行任何執行）。  
  
## <a name="remarks"></a>備註  
 用於`dwThreadState`欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)

