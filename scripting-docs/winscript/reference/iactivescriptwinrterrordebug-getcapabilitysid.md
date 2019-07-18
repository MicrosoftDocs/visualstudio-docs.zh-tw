---
title: IActiveScriptWinRTErrorDebug::GetCapabilitySid | Microsoft Docs
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
ms.openlocfilehash: 6847dba8f2bd3051df4ab6f0940e7b405698e45b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432943"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
如果有的話，會傳回 Windows 執行階段錯誤，功能 SID。  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)是實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>參數  
 `capabilitySid`  
 SID 錯誤的功能。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)