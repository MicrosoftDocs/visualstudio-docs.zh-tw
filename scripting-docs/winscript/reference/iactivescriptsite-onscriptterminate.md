---
title: IActiveScriptSite::OnScriptTerminate |Microsoft Docs
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
ms.openlocfilehash: 664f974b26a2cae0d1e16d37dc3bc66e95993d6f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144819"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
通知主機指令碼已完成執行。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pvarResult`  
 [in]包含指令碼結果中，變數的位址或`NULL`如果指令碼會不產生任何結果。  
  
 `pexcepinfo`  
 [in]位址`EXCEPINFO`結構，其中包含指令碼結束時，所產生的例外狀況資訊或`NULL`如果不產生任何例外狀況。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 指令碼引擎之前呼叫這個方法的呼叫[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法，設定 SCRIPTSTATE_INITIALIZED 旗標，已完成。 這個方法可用來傳回至主機的完成狀態和結果。 請注意，許多指令碼語言，以從主機接收事件為基礎，主應用程式所定義的有效期限。 在此情況下，可能永遠不會呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)