---
title: IActiveScript::GetScriptState |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a64067679e1c56831002494c579ffdeba84a1abe
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096573"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
擷取指令碼引擎的目前狀態。 可以從非基底執行緒呼叫這個方法，不會導致主機物件或非基底圖說[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pss`  
 [out]接收中定義的值，變數的位址[SCRIPTSTATE 列舉](../../winscript/reference/scriptstate-enumeration.md)列舉型別。 值表示呼叫執行緒相關聯的指令碼引擎的目前狀態。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_POINTER`如果指定了無效的指標。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)