---
title: IActiveScript::SetScriptState |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645668"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
將指令碼引擎放入指定的狀態。 可以從非基底執行緒呼叫這個方法，不會導致非基本圖說文字主機物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ss`  
 [in]將指令碼引擎設定為給定的狀態。 可以是其中一個值中定義[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|指令碼引擎不支援為初始化的狀態轉換。 主機必須捨棄此指令碼引擎與建立、 初始化及載入新的指令碼引擎，來達到相同的效果。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化），因此失敗。|  
|`OLESCRIPT_S_PENDING`|方法成功，已佇列但狀態未變更。 當狀態變更時，站台將會呼叫回透過[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。|  
|`S_FALSE`|方法成功，但是指令碼中已存在於指定的狀態。|  
  
## <a name="remarks"></a>備註  
 如需指令碼引擎狀態的詳細資訊，請參閱 > 一節指令碼引擎狀態[Windows 指令碼引擎](../../winscript/windows-script-engines.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)