---
title: IActiveScriptSiteInterruptPoll：： QueryContinue |Microsoft Docs
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
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572232"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
允許主機指定腳本應該終止。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法不接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|呼叫成功，且主機允許腳本繼續執行。|  
|`S_FALSE`|此呼叫成功，且主機要求腳本終止。|  
  
## <a name="remarks"></a>備註  
 除非 `S_OK` `QueryContinue` 方法的傳回值，否則託管的腳本應該會終止。 @No__t_0 的傳回值表示主機會明確要求腳本終止。  
  
 多執行緒主機可以使用 `IActiveScript::InterruptScriptThread` 方法來終止腳本。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSiteInterruptPoll 介面](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)