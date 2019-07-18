---
title: IDebugApplication::HandleRuntimeError |Microsoft Docs
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
ms.openlocfilehash: c2c9a8b15b5095ac346ba047d6668aada7647a31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412429"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
讓目前的執行緒封鎖，並將錯誤的通知傳送至偵錯工具 IDE。  
  
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
 [in]發生錯誤。  
  
 `pScriptSite`  
 [in]執行緒的指令碼網站。  
  
 `pbra`  
 [out]偵錯工具繼續執行應用程式時要採取的動作。  
  
 `perra`  
 [out]偵錯工具繼續應用程式，如果發生錯誤時要採取的動作。  
  
 `pfCallOnScriptError`  
 [out]這是旗標`TRUE`如果應該呼叫引擎`IActiveScriptSite::OnScriptError`方法。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 語言引擎會呼叫這個方法會導致執行階段錯誤的執行緒內容中。 這個方法會導致目前的執行緒可封鎖，並傳送錯誤通知傳送至偵錯工具 IDE。 當偵錯工具 IDE 恢復應用程式時，這個方法會傳回與所要採取的動作。  
  
> [!NOTE]
> 在 執行階段錯誤，語言引擎可能呼叫的執行緒來執行這類工作，因為列舉堆疊框架，或評估運算式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug 介面](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列舉](../../winscript/reference/errorresumeaction-enumeration.md)