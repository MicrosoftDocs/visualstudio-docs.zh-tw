---
title: "IActiveScript::GetScriptThreadState |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b11b8566857bc70aaeac5bdf8e8e357fa5d9c2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
擷取目前執行緒狀態的指令碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stidThread`  
 [in]其想要的狀態，執行緒的識別項或其中一個下列特殊執行緒識別項：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|基底的執行緒，也就是未具現化所在的指令碼引擎的執行緒。|  
|SCRIPTTHREADID_CURRENT|目前執行中執行緒。|  
  
 `pstsState`  
 [out]接收指定的執行緒狀態的變數的位址。 狀態會表示具名常數所定義的值的其中一個[SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md)列舉型別。 如果這個參數不會識別目前的執行緒，可能會隨時變更狀態。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 可以從非基底執行緒呼叫這個方法，不會導致非基本圖說文字主機物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)