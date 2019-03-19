---
title: SCRIPTTHREADID 常數 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfbb39d10d552141a68d40a7be3f1715a80f8f57
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158048"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID 的常數
用來指定執行緒的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|目前正在執行的執行緒。|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|基底執行緒中;也就是已經具現化所在的指令碼引擎的執行緒。|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|所有的執行緒。|  
  
## <a name="remarks"></a>備註  
 `SCRIPTTHREADID`型別由`IActiveScript::GetCurrentScriptThreadID`， `IActiveScript::GetScriptThreadID`， `IActiveScript::GetScriptThreadState`，並`IActiveScript::InterruptScriptThread`，但常數可以僅供`IActiveScript::GetScriptThreadState`並`IActiveScript::InterruptScriptThread`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)