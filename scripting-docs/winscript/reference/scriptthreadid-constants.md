---
title: SCRIPTTHREADID 的常數 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734188"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID 的常數
用來指定執行緒的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>常數  
  
|常數|值|意義|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|目前執行中執行緒。|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|基底的執行緒，也就是未具現化所在的指令碼引擎的執行緒。|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|所有執行緒。|  
  
## <a name="remarks"></a>備註  
 `SCRIPTTHREADID`類型正由`IActiveScript::GetCurrentScriptThreadID`， `IActiveScript::GetScriptThreadID`， `IActiveScript::GetScriptThreadState`，和`IActiveScript::InterruptScriptThread`，但常數可以只供`IActiveScript::GetScriptThreadState`和`IActiveScript::InterruptScriptThread`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)