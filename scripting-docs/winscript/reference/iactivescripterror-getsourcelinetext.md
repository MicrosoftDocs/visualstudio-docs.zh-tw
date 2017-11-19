---
title: "IActiveScriptError::GetSourceLineText |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb886d5f40042313483dc3b298488d1291c30563
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
擷取錯誤發生時，指令碼引擎執行指令碼時的原始程式檔中的一行。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>參數  
 `pbstrSourceLine`  
 [out]接收的來源發生錯誤的程式碼行緩衝區的位址。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，或`E_FAIL`如果原始程式檔中的行，所以無法擷取。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)