---
title: IActiveScriptError::GetSourcePosition |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157681"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
擷取在原始程式碼中發生錯誤時，指令碼引擎所執行的指令碼的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwSourceContext`  
 [out]會接收 cookie 來識別的內容變數的位址。 此參數的解譯取決於主應用程式。  
  
 `pulLineNumber`  
 [out]接收發生錯誤的原始程式檔中的行號的變數位址。  
  
 `pichCharPosition`  
 [out]此變數會接收發生錯誤的字元位置的行中的位址。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_FAIL`如果位置，所以無法擷取。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)