---
title: IActiveScriptSite：： OnEnterScript |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570359"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
通知主機腳本引擎已開始執行腳本。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 腳本引擎必須在每個專案上呼叫此方法，或將它重入腳本引擎。 例如，如果腳本呼叫的物件接著會引發腳本引擎所處理的事件，則腳本引擎必須在執行事件之前呼叫 `IActiveScriptSite::OnEnterScript`，而且必須在執行事件之後呼叫[IActiveScriptSite：： OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)方法。但在回到引發事件的物件之前。 這個方法的呼叫可以進行嵌套。 每次呼叫此方法時，都需要對應的 `IActiveScriptSite::OnLeaveScript` 呼叫。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)