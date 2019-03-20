---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa46bc95087b3defaf739cc3473c58e29a93071c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155926"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
中斷執行指令碼中的執行緒 （事件接收器、 立即執行或的巨集引動過程） 的執行。 這個方法可用來終止卡 （例如，在無限迴圈） 的指令碼。 可以從非基底執行緒中呼叫不會導致主機物件或非基底圖說[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stidThread`  
 [in]要中斷或其中一個下列特殊的執行緒識別碼值的執行緒識別碼：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|所有的執行緒。 中斷會套用至正在進行中的所有指令碼方法。 請注意，除非呼叫者已要求指令碼會中斷下, 一個已編寫指令碼的事件會使指令碼，以再次執行，藉由呼叫[iactivescript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) SCRIPTSTATE_DISCONNECTED 方法或設定 SCRIPTSTATE_INITIALIZED 旗標。|  
|SCRIPTTHREADID_BASE|基底執行緒中;也就是已經具現化所在的指令碼引擎的執行緒。|  
|SCRIPTTHREADID_CURRENT|目前正在執行的執行緒。|  
  
 `pexcepinfo`  
 [in]位址`EXCEPINFO`結構，其中包含已中止的指令碼就應該報告的錯誤資訊。  
  
 `dwFlags`  
 [in]中斷與相關聯的選項旗標。 可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|如果支援，請輸入指令碼引擎的偵錯工具，在目前的指令碼執行時間點。|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|如果指令碼引擎的語言支援，讓指令碼處理例外狀況。 否則，指令碼方法會中止，並呼叫端; 傳回的錯誤碼也就是事件來源或巨集啟動程式。|  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化）。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)