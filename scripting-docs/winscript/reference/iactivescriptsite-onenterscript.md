---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccef1b2bf63c4421843d3a33cab2e4f471a48251
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346510"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
通知主機，指令碼引擎已開始執行的指令碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 指令碼引擎必須呼叫這個方法在每個項目或重新進入到指令碼引擎。 例如，如果指令碼會呼叫物件，然後引發由指令碼引擎處理事件，指令碼引擎必須呼叫`IActiveScriptSite::OnEnterScript`之前執行事件，以及必須呼叫[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)在執行事件之後，但傳回，這個物件會引發事件之前的方法。 呼叫此方法可以是巢狀。 每次呼叫此方法需要對應呼叫`IActiveScriptSite::OnLeaveScript`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)