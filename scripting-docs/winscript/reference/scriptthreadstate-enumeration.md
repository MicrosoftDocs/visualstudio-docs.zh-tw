---
title: "SCRIPTTHREADSTATE 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE 列舉
指定在指令碼引擎的執行緒的狀態。 這個列舉型別由[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|指定的執行緒目前不是服務的已編寫指令碼的事件處理立即執行指令碼文字，或執行指令碼的巨集。|  
|SCRIPTTHREADSTATE_RUNNING|指定的執行緒正在服務已編寫指令碼的事件，立即執行的處理指令碼文字，或執行指令碼的巨集。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)