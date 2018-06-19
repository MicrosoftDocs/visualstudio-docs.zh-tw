---
title: IActiveScriptSite::OnScriptTerminate |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724798"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
通知主機在指令碼已完成執行。  
  
## <a name="syntax"></a>語法  
  
```  
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
 指令碼引擎會呼叫這個方法的呼叫之前[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)方法，設定 SCRIPTSTATE_INITIALIZED 旗標，會完成。 這個方法可以用來傳回至主機的完成狀態和結果。 請注意，許多的指令碼語言，根據從主機接收事件，會由主應用程式的期限。 在此情況下，可能永遠不會呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)