---
title: IActiveScript::GetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f9f3bedee9af9ae3cb145108d801f252267d5d2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156979"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
擷取指令碼引擎的目前狀態。 可以從非基底執行緒呼叫這個方法，不會導致主機物件或非基底圖說[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pss`  
 [out]接收中定義的值，變數的位址[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉型別。 值表示呼叫執行緒相關聯的指令碼引擎的目前狀態。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_POINTER`如果指定了無效的指標。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)