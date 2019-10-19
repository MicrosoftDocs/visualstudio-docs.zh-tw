---
title: IActiveScriptSiteDebugEx：： OnCanNotJITScriptErrorDebug |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572176"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
當進程 Debug Manager 找不到即時腳本偵錯工具時，通知主機關於腳本執行階段錯誤。  
  
 若要在您的主機中執行偵錯工具，您應該處理[IActiveScriptSiteDebug：： OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)。 根據使用者動作，主機可以附加偵錯工具並傳回，或傳回 OnScriptErrorDebug `pfEnterDebugger` 參數中的偵錯工具啟動。 您也應該執行此介面來取得有關執行階段錯誤的通知，即使沒有可由進程 Debug Manager 來解讀的外部偵錯工具也一樣。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pErrorDebug`  
 在發生的執行階段錯誤。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 脫銷如果使用者決定繼續而不進行調試，是否要呼叫[IActiveScriptSiteDebug：： OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) 。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 您也應該執行此介面來取得通知。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSiteDebugEx 介面](../../winscript/reference/iactivescriptsitedebugex-interface.md)