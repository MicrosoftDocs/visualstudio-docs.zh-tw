---
title: IDebugApplication：： HandleRuntimeError |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574324"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
導致目前的執行緒封鎖並傳送錯誤通知給偵錯工具 IDE。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pErrorDebug`  
 在發生的錯誤。  
  
 `pScriptSite`  
 在執行緒的腳本網站。  
  
 `pbra`  
 脫銷當偵錯工具繼續應用程式時所要採取的動作。  
  
 `perra`  
 脫銷當偵錯工具在發生錯誤時繼續執行時，所要採取的動作。  
  
 `pfCallOnScriptError`  
 脫銷如果引擎應呼叫 `IActiveScriptSite::OnScriptError` 方法，則為 `TRUE` 旗標。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會在造成執行階段錯誤的執行緒內容中呼叫這個方法。 這個方法會導致目前的執行緒封鎖，並傳送錯誤通知給偵錯工具 IDE。 當偵錯工具 IDE 繼續執行應用程式時，這個方法會傳回，其中包含要採取的動作。  
  
> [!NOTE]
> 雖然在執行時間錯誤中，執行緒可能會呼叫語言引擎來執行這類工作，例如列舉堆疊框架或評估運算式。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)    
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列舉](../../winscript/reference/errorresumeaction-enumeration.md)