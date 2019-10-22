---
title: IActiveScript：： GetScriptState |Microsoft Docs
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
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575729"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
抓取腳本引擎的目前狀態。 這個方法可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pss`  
 脫銷接收[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉中所定義之值的變數位址。 此值表示與呼叫執行緒相關聯之腳本引擎的目前狀態。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果指定了不正確指標，則傳回 `E_POINTER`。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)