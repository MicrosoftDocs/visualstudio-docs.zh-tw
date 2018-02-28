---
title: "BREAKRESUMEACTION 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION 列舉
描述從中斷點繼續執行的方式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|中止應用程式。|  
|BREAKRESUMEACTION_CONTINUE|繼續執行。|  
|BREAKRESUMEACTION_STEP_INTO|逐步執行程序。|  
|BREAKRESUMEACTION_STEP_OVER|不進入程序。|  
|BREAKRESUMEACTION_STEP_OUT|跳離目前的程序。|  
|BREAKRESUMEACTION_IGNORE|在狀態下繼續執行。|  
|BREAKRESUMEACTION_STEP_DOCUMENT|繼續執行下一個文件。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)