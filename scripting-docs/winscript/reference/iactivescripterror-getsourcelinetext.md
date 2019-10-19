---
title: IActiveScriptError：： GetSourceLineText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ded57f97ec40167bac34bf0f288c2e3d15a5c4b7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576909"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
當腳本引擎執行腳本時，抓取原始程式檔中發生錯誤的行。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>參數  
 `pbstrSourceLine`  
 脫銷接收發生錯誤之源程式碼的緩衝區位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 `S_OK`，如果未抓取原始程式檔中的行，則傳回 `E_FAIL`。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)