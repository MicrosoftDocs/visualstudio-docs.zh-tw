---
title: SCRIPTTHREADSTATE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575648"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE 列舉
指定腳本引擎中的執行緒狀態。 [IActiveScript：： GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)方法會使用這個列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>列舉值  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|指定的執行緒目前未提供已編寫腳本的事件、處理立即執行的腳本文字，或正在執行腳本宏。|  
|SCRIPTTHREADSTATE_RUNNING|指定的執行緒正在主動服務已編寫腳本的事件、處理立即執行的腳本文字，或執行腳本宏。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼的常數、列舉和錯誤碼](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)