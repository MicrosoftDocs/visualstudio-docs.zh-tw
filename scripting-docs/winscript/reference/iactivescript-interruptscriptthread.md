---
title: "IActiveScript::InterruptScriptThread |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
會中斷執行的執行指令碼中的執行緒 （事件接收器、 立即執行或巨集引動）。 這個方法可以用來終止卡 （例如，在無限迴圈） 的指令碼。 可以從非基底執行緒中呼叫不會導致非基本圖說文字主機物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stidThread`  
 [in]要中斷或下列特殊執行緒識別碼值的其中一個執行緒的識別項：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|所有執行緒。 插斷會套用至目前正在進行的所有指令碼方法。 請注意，除非呼叫端就已要求指令碼會中斷連線下, 一個已編寫指令碼的事件會使指令碼，以再次執行，藉由呼叫[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) SCRIPTSTATE_DISCONNECTED 具有方法或設定 SCRIPTSTATE_INITIALIZED 旗標。|  
|SCRIPTTHREADID_BASE|基底的執行緒，也就是未具現化所在的指令碼引擎的執行緒。|  
|SCRIPTTHREADID_CURRENT|目前執行中執行緒。|  
  
 `pexcepinfo`  
 [in]位址`EXCEPINFO`結構，其中包含應該報告已中止的指令碼的錯誤資訊。  
  
 `dwFlags`  
 [in]中斷與相關聯的選項旗標。 可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|如果支援，請輸入指令碼引擎偵錯工具在目前的指令碼執行時間點。|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|如果指令碼引擎的語言支援，可讓指令碼處理例外狀況。 否則，就會中止指令碼方法和錯誤碼傳回至呼叫端;也就是說，事件來源或巨集啟動程式。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)