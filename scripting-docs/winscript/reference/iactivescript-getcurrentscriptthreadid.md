---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bac3b5755328e643c26c8f3746af6648d8ac06aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345795"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
擷取目前執行中執行緒的指令碼引擎-定義識別項。 識別項可用於指令碼的執行緒執行控制方法的後續呼叫這類[iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstidThread`  
 [out]接收與目前執行緒相關聯的指令碼的執行緒識別碼的變數位址。 這個識別項的解譯會保留給指令碼引擎，但它可以是只是 Windows 執行緒識別碼的複本。 如果 Win32 執行緒終止時，此識別碼會變成未指派，並接著可以指派至另一個執行緒。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_POINTER`如果指定了無效的指標。  
  
## <a name="remarks"></a>備註  
 可以從非基底執行緒呼叫這個方法，不會導致主機物件或非基底圖說[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)