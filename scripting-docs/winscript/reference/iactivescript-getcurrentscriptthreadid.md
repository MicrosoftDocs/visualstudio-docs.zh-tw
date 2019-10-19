---
title: IActiveScript：： GetCurrentScriptThreadID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575771"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
針對目前執行中的執行緒，抓取腳本引擎定義的識別碼。 在後續呼叫腳本執行緒執行控制方法（例如[IActiveScript：： InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法）時，可以使用此識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstidThread`  
 脫銷接收與目前線程相關聯之腳本執行緒識別碼的變數位址。 此識別碼的解讀會留給腳本引擎，但它可以只是 Windows 執行緒識別碼的複本。 如果 Win32 執行緒終止，此識別碼就會變成未指派，並可接著指派給另一個執行緒。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果指定了不正確指標，則傳回 `E_POINTER`。  
  
## <a name="remarks"></a>備註  
 這個方法可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)