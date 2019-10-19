---
title: IActiveScriptSiteDebug：： OnScriptErrorDebug |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572213"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
允許智慧型主機判斷如何處理執行階段錯誤。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pErrorDebug`  
 在發生的執行階段錯誤  
  
 `pfEnterDebugger`  
 脫銷旗標，指出是否要將錯誤傳遞給偵錯工具，以執行 JIT 的偵錯工具。  
  
 `pfCallOnScriptErrorWhenContinuing`  
 脫銷旗標，指出當使用者決定繼續而不進行調試時，是否要呼叫 `IActiveScriptSite::OnScriptError`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括，但不限於下表中的值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 智慧型主機可以使用這個方法來判斷如何處理執行階段錯誤。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)