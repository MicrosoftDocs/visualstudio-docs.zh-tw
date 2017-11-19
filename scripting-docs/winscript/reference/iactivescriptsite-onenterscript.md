---
title: "IActiveScriptSite::OnEnterScript |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
通知主機指令碼引擎已開始執行指令碼的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 指令碼引擎必須呼叫這個方法上每個項目或重新進入指令碼引擎。 例如，如果指令碼，呼叫物件，然後引發由指令碼引擎所處理的事件，指令碼引擎必須呼叫`IActiveScriptSite::OnEnterScript`之前執行事件，並必須呼叫[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)執行事件後再傳回，這個物件會引發此事件的方法。 呼叫此方法可以是巢狀。 每次呼叫此方法需要對應呼叫`IActiveScriptSite::OnLeaveScript`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)