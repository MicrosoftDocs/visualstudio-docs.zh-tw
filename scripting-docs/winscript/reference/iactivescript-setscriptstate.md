---
title: IActiveScript：： SetScriptState |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577995"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
將腳本引擎放入指定的狀態。 這個方法可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ss`  
 在將腳本引擎設定為指定的狀態。 可以是[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉中所定義的其中一個值。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|腳本引擎不支援轉換回已初始化的狀態。 主機必須捨棄此腳本引擎，並建立、初始化和載入新的腳本引擎，以達到相同的效果。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化），因此失敗。|  
|`OLESCRIPT_S_PENDING`|已成功將方法排入佇列，但狀態尚未變更。 當狀態變更時，會透過[IActiveScriptSite：： OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法來回呼網站。|  
|`S_FALSE`|方法成功，但腳本已處於指定的狀態。|  
  
## <a name="remarks"></a>備註  
 如需腳本引擎狀態的詳細資訊，請參閱[Windows 腳本引擎](../../winscript/windows-script-engines.md)的腳本引擎狀態一節。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript：： Clone](../../winscript/reference/iactivescript-clone.md)    
 [IActiveScript：： GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)    
 [IActiveScript：： InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)    
 [IActiveScriptParse：:P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)