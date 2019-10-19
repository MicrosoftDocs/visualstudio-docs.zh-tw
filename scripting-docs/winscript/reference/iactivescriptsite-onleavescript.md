---
title: IActiveScriptSite：： OnLeaveScript |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570326"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
通知主機腳本引擎已從執行腳本傳回。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="remarks"></a>備註  
 腳本引擎必須先呼叫這個方法，然後再將控制權傳回給進入腳本引擎的呼叫應用程式。 例如，如果腳本呼叫的物件接著會引發腳本引擎所處理的事件，則腳本引擎必須在執行事件之前呼叫[IActiveScriptSite：： OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)方法，而且必須在執行事件之後呼叫 `IActiveScriptSite::OnLeaveScript`返回引發事件的物件之前。 這個方法的呼叫可以進行嵌套。 @No__t_0 的每個呼叫都需要對這個方法進行對應的呼叫。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)