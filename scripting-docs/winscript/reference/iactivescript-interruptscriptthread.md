---
title: IActiveScript：： InterruptScriptThread |Microsoft Docs
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
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577271"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
中斷執行中腳本執行緒（事件接收、立即執行或宏調用）的執行。 這個方法可以用來結束停滯的腳本（例如，在無限迴圈中）。 它可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)方法。  
  
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
 在要中斷之執行緒的識別碼，或下列其中一個特殊的執行緒識別碼值：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|所有線程。 中斷會套用到目前進行中的所有腳本方法。 請注意，除非呼叫端已要求將腳本中斷連接，否則下一個腳本事件會呼叫[IActiveScript：： SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)方法與 SCRIPTSTATE_DISCONNECTED 或 SCRIPTSTATE_INITIALIZED 旗標，以再次執行腳本程式碼設定.|  
|SCRIPTTHREADID_BASE|基底線程;也就是在其中具現化腳本引擎的執行緒。|  
|SCRIPTTHREADID_CURRENT|目前執行的執行緒。|  
  
 `pexcepinfo`  
 在包含應回報給已中止腳本之錯誤資訊的 `EXCEPINFO` 結構的位址。  
  
 `dwFlags`  
 在與中斷相關聯的選項旗標。 可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|如果支援，請在目前的腳本執行點上輸入腳本引擎的偵錯工具。|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|如果腳本引擎的語言支援，請讓腳本處理例外狀況。 否則，腳本方法會中止，且錯誤碼會傳回給呼叫者;也就是事件來源或宏啟動程式。|  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)