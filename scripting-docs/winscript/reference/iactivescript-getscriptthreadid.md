---
title: IActiveScript：： GetScriptThreadID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575710"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
針對與指定的 Win32 執行緒相關聯的執行緒，抓取腳本引擎定義的識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwWin32ThreadID` ,  
 在目前進程中執行中 Win32 執行緒的執行緒識別碼。 使用[IActiveScript：： GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)函式來抓取目前正在執行之執行緒的執行緒識別碼。  
  
 `pstidThread` ,  
 脫銷接收與指定的 Win32 執行緒相關聯之腳本執行緒識別碼的變數位址。 此識別碼的解讀會留給腳本引擎，但它可以只是 Windows 執行緒識別碼的複本。 請注意，如果 Win32 執行緒終止，此識別碼就會變成未指派，而且之後可能會指派給另一個執行緒。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化），因此失敗。|  
  
## <a name="remarks"></a>備註  
 抓取的識別碼可用於腳本執行緒執行控制方法的後續呼叫，例如[IActiveScript：： InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
 這個方法可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScript：： InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)介面。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)