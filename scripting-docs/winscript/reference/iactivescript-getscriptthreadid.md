---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935688"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
擷取與指定的 Win32 執行緒相關聯執行緒的指令碼引擎-定義識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwWin32ThreadID` ,  
 [in]目前的處理序中執行的 Win32 執行緒的執行緒識別項。 使用[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)函式來擷取目前執行中執行緒的執行緒識別碼。  
  
 `pstidThread` ,  
 [out]接收指定的 Win32 執行緒相關聯的指令碼執行緒識別碼的變數位址。 這個識別項的解譯會保留給指令碼引擎，但它可以是只是 Windows 執行緒識別碼的複本。 請注意，是否 Win32 執行緒終止時，這個識別碼就會變成未指派，接著可能會指派到另一個執行緒。  
  
## <a name="return-value"></a>傳回值  
 會傳回下列值之一：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_POINTER`|指定了無效的指標。|  
|`E_UNEXPECTED`|不需要呼叫 （例如，指令碼引擎有尚未載入或初始化），因此失敗。|  
  
## <a name="remarks"></a>備註  
 擷取的識別碼可用於指令碼的執行緒執行控制方法的後續呼叫這類[iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)方法。  
  
 可以從非基底執行緒呼叫這個方法，不會導致主機物件或非基底圖說[iactivescript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)