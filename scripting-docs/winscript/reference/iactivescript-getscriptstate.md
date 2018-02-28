---
title: "IActiveScript::GetScriptState |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285a09308c7477dbeed68f9f93417b503ca4fe49
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
擷取指令碼引擎的目前的狀態。 可以從非基底執行緒呼叫這個方法，不會導致非基本圖說文字主機物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pss`  
 [out]收到的值中定義的變數位址[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉型別。 值表示呼叫執行緒相關聯的指令碼引擎的目前狀態。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_POINTER`如果指定了無效的指標。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)