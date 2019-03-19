---
title: IActiveScriptSiteInterruptPoll::QueryContinue |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 63ce45c0973d65d240136d7b42aef0c078b00c9a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154305"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
可讓主應用程式指定指令碼應該結束。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|呼叫成功，並在主機允許繼續執行指令碼。|  
|`S_FALSE`|呼叫成功，指令碼終止主機要求。|  
  
## <a name="remarks"></a>備註  
 除非 「 應該 」 終止裝載的指令碼的傳回值`QueryContinue`方法是`S_OK`。 傳回值為`S_FALSE`指出，主應用程式明確要求指令碼結束。  
  
 多執行緒的主應用程式可能使用`IActiveScript::InterruptScriptThread`終止指令碼的方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSiteInterruptPoll 介面](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)