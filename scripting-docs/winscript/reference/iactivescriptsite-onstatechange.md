---
title: IActiveScriptSite::OnStateChange |Microsoft Docs
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
ms.openlocfilehash: ee4fd06b00c674c9c50ce253186aeee3165bac66
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097405"
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
通知主機指令碼引擎已變更狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ssScriptState`  
 [in]值，指出新的指令碼狀態。 請參閱[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)方法，如需狀態的描述。  
  
## <a name="return-value"></a>傳回值  
 若成功，會傳回 `S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)