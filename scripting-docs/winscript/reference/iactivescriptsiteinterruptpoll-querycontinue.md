---
title: IActiveScriptSiteInterruptPoll::QueryContinue |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725158"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
可讓主應用程式指定指令碼應該結束。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|呼叫成功，且主機可允許繼續執行指令碼。|  
|`S_FALSE`|成功的呼叫和指令碼終止主機要求。|  
  
## <a name="remarks"></a>備註  
 裝載的指令碼應該結束，除非傳回值`QueryContinue`方法`S_OK`。 傳回值為`S_FALSE`指出，在主機明確要求指令碼結束。  
  
 多執行緒的主機可能會使用`IActiveScript::InterruptScriptThread`終止指令碼的方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteInterruptPoll 介面](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)