---
title: "IDebugApplication::HandleRuntimeError |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
會導致目前的執行緒可封鎖，並將錯誤的通知傳送至 IDE 偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]發生的錯誤。  
  
 `pScriptSite`  
 [in]執行緒的指令碼站台。  
  
 `pbra`  
 [out]偵錯工具會繼續執行應用程式時要採取的動作。  
  
 `perra`  
 [out]偵錯工具繼續應用程式，如果發生錯誤時要採取的動作。  
  
 `pfCallOnScriptError`  
 [out]這是旗標`TRUE`如果應該呼叫引擎`IActiveScriptSite::OnScriptError`方法。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會呼叫這個方法會導致執行階段錯誤的執行緒內容中。 這個方法會導致目前的執行緒可封鎖，並將傳送至偵錯工具 IDE 錯誤通知。 當 IDE 偵錯工具會繼續執行應用程式時，這個方法會傳回與所要採取的動作。  
  
> [!NOTE]
>  執行階段錯誤中, 語言引擎可能會被呼叫執行緒來執行這類工作，因為列舉堆疊框架，或評估的運算式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列舉](../../winscript/reference/errorresumeaction-enumeration.md)