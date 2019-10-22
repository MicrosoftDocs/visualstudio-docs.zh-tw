---
title: BREAKREASON 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572630"
---
# <a name="breakreason-enumeration"></a>BREAKREASON 列舉
指出造成中斷的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|BREAKREASON_STEP|語言引擎處於逐步執行模式。|  
|BREAKREASON_BREAKPOINT|語言引擎發現明確的中斷點。|  
|BREAKREASON_DEBUGGER_BLOCK|語言引擎在另一個執行緒上遇到偵錯工具區塊。|  
|BREAKREASON_HOST_INITIATED|主機已要求中斷。|  
|BREAKREASON_LANGUAGE_INITIATED|語言引擎要求中斷。|  
|BREAKREASON_DEBUGGER_HALT|偵錯工具 IDE 已要求中斷。|  
|BREAKREASON_ERROR|執行錯誤造成中斷。|  
|BREAKREASON_JIT|JIT 偵錯程式啟動造成的。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)