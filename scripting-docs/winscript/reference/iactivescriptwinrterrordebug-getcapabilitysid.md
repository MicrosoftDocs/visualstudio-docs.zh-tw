---
title: IActiveScriptWinRTErrorDebug：： GetCapabilitySid |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93bf824dd4d290ca536cb609e24b5d14400a3e3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577925"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
傳回 Windows 執行階段錯誤的功能 SID （如果有的話）。  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>參數  
 `capabilitySid`  
 錯誤的功能 SID。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)