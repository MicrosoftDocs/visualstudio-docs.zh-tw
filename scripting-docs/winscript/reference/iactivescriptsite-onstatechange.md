---
title: IActiveScriptSite::OnStateChange |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae7782d713ab226e57e687cda8eb4ccdb54cf20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724618"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
通知主機指令碼引擎已變更狀態。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ssScriptState`  
 [in]值，指出新的指令碼狀態。 請參閱[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)方法狀態的描述。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)