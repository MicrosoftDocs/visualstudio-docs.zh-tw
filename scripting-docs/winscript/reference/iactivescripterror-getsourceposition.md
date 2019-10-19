---
title: IActiveScriptError：： GetSourcePosition |Microsoft Docs
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
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576889"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
當腳本引擎執行腳本時，抓取原始程式碼中發生錯誤的位置。  
  
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
 脫銷接收識別內容之 cookie 的變數位址。 這個參數的轉譯取決於主應用程式。  
  
 `pulLineNumber`  
 脫銷在發生錯誤的原始程式檔中，接收行號之變數的位址。  
  
 `pichCharPosition`  
 脫銷在發生錯誤的行中，接收字元位置的變數位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果未抓取位置，則傳回 `E_FAIL`。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)