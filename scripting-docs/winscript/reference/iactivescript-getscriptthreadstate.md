---
title: IActiveScript：： GetScriptThreadState |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578001"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
抓取腳本執行緒的目前狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stidThread`  
 在需要狀態之執行緒的識別碼，或下列其中一個特殊執行緒識別碼：  
  
|值|意義|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|基底線程;也就是在其中具現化腳本引擎的執行緒。|  
|SCRIPTTHREADID_CURRENT|目前執行的執行緒。|  
  
 `pstsState`  
 脫銷接收指定之執行緒狀態的變數位址。 狀態是由[SCRIPTTHREADSTATE 列舉](../../winscript/reference/scriptthreadstate-enumeration.md)列舉所定義的其中一個已命名的常數值所表示。 如果此參數未識別目前的執行緒，則狀態可能會隨時變更。  
  
## <a name="return-value"></a>傳回值  
 傳回下列其中一個值：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了不正確指標。|  
|`E_UNEXPECTED`|不需要呼叫（例如，腳本引擎尚未載入或初始化）。|  
  
## <a name="remarks"></a>備註  
 這個方法可以從非基底線程呼叫，而不會產生非基底的標注來裝載物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)