---
title: "IActiveScriptSite::OnLeaveScript |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
通知主機指令碼引擎已執行的指令碼傳回。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 指令碼引擎必須呼叫這個方法，然後再將控制權傳回給呼叫的應用程式中輸入指令碼引擎。 例如，如果指令碼，呼叫物件，然後引發由指令碼引擎所處理的事件，指令碼引擎必須呼叫[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)方法，然後再執行事件，必須呼叫`IActiveScriptSite::OnLeaveScript`後再傳回給引發事件的物件執行事件。 呼叫此方法可以是巢狀。 每次呼叫`IActiveScriptSite::OnEnterScript`需要對應呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)