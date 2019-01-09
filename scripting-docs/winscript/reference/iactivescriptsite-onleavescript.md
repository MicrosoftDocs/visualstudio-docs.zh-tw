---
title: IActiveScriptSite::OnLeaveScript |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d08d58fc788d2d10ed044808ca40a5f4ea929c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093154"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
無法執行指令碼程式碼，傳回指令碼引擎通知主機。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 指令碼引擎必須呼叫這個方法，再將控制權傳回給呼叫的應用程式中輸入指令碼引擎。 例如，如果指令碼會呼叫物件，然後引發由指令碼引擎處理事件，指令碼引擎必須呼叫[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)方法，然後再執行事件，必須呼叫`IActiveScriptSite::OnLeaveScript`之後執行之前傳回，這個物件會引發事件的事件。 呼叫此方法可以是巢狀。 每次呼叫`IActiveScriptSite::OnEnterScript`需要對應至這個方法的呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)