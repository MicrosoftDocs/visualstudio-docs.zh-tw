---
title: "IActiveScript::GetCurrentScriptThreadID |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
擷取目前執行中執行緒的指令碼引擎-定義識別項。 識別項可以用於指令碼的執行緒執行控制方法的後續呼叫這類[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pstidThread`  
 [out]接收與目前執行緒相關聯的指令碼的執行緒識別碼的變數的位址。 此識別碼解譯工作留給指令碼引擎，但它可以是只是 Windows 執行緒識別碼的複本。 如果終止的 Win32 執行緒，此識別碼會成為未指派，並接著可以指派給另一個執行緒。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_POINTER`如果指定了無效的指標。  
  
## <a name="remarks"></a>備註  
 可以從非基底執行緒呼叫這個方法，不會導致非基本圖說文字主機物件或[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)