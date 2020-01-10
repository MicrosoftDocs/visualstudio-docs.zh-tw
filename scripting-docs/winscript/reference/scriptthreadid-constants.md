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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575672"
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
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|目前執行的執行緒。|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|基底線程;也就是在其中具現化腳本引擎的執行緒。|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|所有線程。|  
  
## <a name="remarks"></a>備註  
 `SCRIPTTHREADID` 類型是由 `IActiveScript::GetCurrentScriptThreadID`、`IActiveScript::GetScriptThreadID`、`IActiveScript::GetScriptThreadState`和 `IActiveScript::InterruptScriptThread`所使用，但常數只能由 `IActiveScript::GetScriptThreadState` 和 `IActiveScript::InterruptScriptThread`使用。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript：： GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript：： GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript：： GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)