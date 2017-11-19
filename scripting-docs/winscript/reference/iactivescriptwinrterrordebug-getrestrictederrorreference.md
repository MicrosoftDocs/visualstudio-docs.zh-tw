---
title: "IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
ms.assetid: fcf60971-9518-4b24-a3a6-1e2e30a02cea
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36d1fecfa1069836a3a1eb41adc8fb58a16e1dbc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorreference"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference
如果有的話，Windows 執行階段傳回限制參考錯誤。  
  
> [!IMPORTANT]
>  [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)會實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRestrictedErrorReference([out] BSTR * referenceString);  
```  
  
#### <a name="parameters"></a>參數  
 `referenceString`  
 [out]參考錯誤字串。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)