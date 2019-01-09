---
title: 'Iactivescript:: Setscriptstate |Microsoft Docs'
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
ms.openlocfilehash: 58edef17fec1d94a09b327dff626658c42a273ba
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095026"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
指令碼引擎放在指定的狀態。 可以從非基底執行緒呼叫這個方法，不會導致主機物件或非基底圖說[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ss`  
 [in]將指令碼引擎設定為指定的狀態。 可以是其中一個值中定義[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉型別。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_FAIL`|指令碼引擎不支援為初始化的狀態轉換。 主機必須捨棄此指令碼引擎並建立、 初始化及載入新的指令碼引擎，來達到相同的效果。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化），因此失敗。|  
|`OLESCRIPT_S_PENDING`|方法已排入佇列成功，但是狀態未變更。 當狀態變更站台會傳回透過呼叫[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法。|  
|`S_FALSE`|此方法成功，但指令碼已存在於指定的狀態。|  
  
## <a name="remarks"></a>備註  
 如需指令碼引擎狀態的詳細資訊，請參閱指令碼引擎狀態一節[Windows 指令碼引擎](../../winscript/windows-script-engines.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Iactivescript:: Clone](../../winscript/reference/iactivescript-clone.md)   
 [Iactivescript:: Getscriptdispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [Iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [Iactivescriptparse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)