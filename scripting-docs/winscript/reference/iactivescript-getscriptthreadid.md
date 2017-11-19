---
title: "IActiveScript::GetScriptThreadID |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
擷取與指定的 Win32 執行緒相關聯的執行緒指令碼引擎-定義識別項。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwWin32ThreadID` ,  
 [in]執行緒目前的處理序中執行的 Win32 執行緒的識別項。 使用[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)函式可擷取目前執行中執行緒的執行緒識別項。  
  
 `pstidThread` ,  
 [out]接收指令碼的執行緒識別項與給定的 Win32 執行緒相關聯的變數的位址。 此識別碼解譯工作留給指令碼引擎，但它可以是只是 Windows 執行緒識別碼的複本。 請注意，是否 Win32 執行緒結束，這個識別碼就會變成未指定，後續可能會指派給另一個執行緒。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不應該呼叫 （例如，指令碼引擎有尚未載入或初始化），因此失敗。|  
  
## <a name="remarks"></a>備註  
 擷取的識別碼可用於指令碼的執行緒執行控制方法的後續呼叫這類[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
 可以從非基底執行緒呼叫這個方法，不會導致非基本圖說文字主機物件或[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)