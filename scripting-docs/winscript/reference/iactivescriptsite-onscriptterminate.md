---
title: IActiveScriptSite：： OnScriptTerminate |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570212"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
通知主機腳本已完成執行。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvarResult`  
 在包含腳本結果之變數的位址，如果腳本沒有產生任何結果，則為 `NULL`。  
  
 `pexcepinfo`  
 在@No__t_0 結構的位址，其中包含腳本終止時所產生的例外狀況資訊，或在未產生任何例外狀況時 `NULL`。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 腳本引擎會在呼叫[IActiveScriptSite：： OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法之前呼叫這個方法，並將 SCRIPTSTATE_INITIALIZED 旗標設定為 completed。 這個方法可以用來將完成狀態和結果傳回給主機。 請注意，許多以主機事件為基礎的指令碼語言，都有主機所定義的生命週期。 在此情況下，可能永遠不會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)