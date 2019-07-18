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
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955404"
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|BREAKREASON_STEP|語言引擎正在逐步執行模式。|  
|BREAKREASON_BREAKPOINT|語言引擎發現明確的中斷點。|  
|BREAKREASON_DEBUGGER_BLOCK|語言引擎遇到另一個執行緒上的偵錯工具區塊。|  
|BREAKREASON_HOST_INITIATED|主機要求中斷。|  
|BREAKREASON_LANGUAGE_INITIATED|語言引擎會要求中斷。|  
|BREAKREASON_DEBUGGER_HALT|偵錯工具 IDE 要求中斷。|  
|BREAKREASON_ERROR|執行錯誤會造成中斷。|  
|BREAKREASON_JIT|因為 JIT 偵錯啟動所造成。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)