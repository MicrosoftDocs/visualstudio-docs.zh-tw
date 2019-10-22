---
title: IActiveScriptError：： GetExceptionInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f776a5f1a60b1280ab1f133ead04fb275782e5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576946"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
抓取腳本引擎執行腳本時發生之錯誤的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pexcepinfo`  
 脫銷接收錯誤資訊之 `EXCEPINFO` 結構的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果發生錯誤，則傳回 `E_FAIL`。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)