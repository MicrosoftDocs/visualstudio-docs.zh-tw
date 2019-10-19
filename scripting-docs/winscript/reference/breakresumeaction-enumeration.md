---
title: BREAKRESUMEACTION 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572617"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION 列舉
描述從中斷點繼續執行的方式。  
  
## <a name="syntax"></a>語法  
  
```cpp
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|中止應用程式。|  
|BREAKRESUMEACTION_CONTINUE|繼續執行。|  
|BREAKRESUMEACTION_STEP_INTO|逐步執行程序。|  
|BREAKRESUMEACTION_STEP_OVER|不進入程序。|  
|BREAKRESUMEACTION_STEP_OUT|跳離目前的程序。|  
|BREAKRESUMEACTION_IGNORE|在狀態下繼續執行。|  
|BREAKRESUMEACTION_STEP_DOCUMENT|繼續執行下一個文件。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)