---
title: IActiveScriptWinRTErrorDebug：： GetRestrictedErrorString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 498d929fb06eea1d6717bfdecb09107bbdaafd98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577897"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
傳回 Windows 執行階段限制的錯誤字串（如果有的話）。  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>參數  
 `errorString`  
 脫銷受限制的錯誤字串。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptWinRTErrorDebug 介面](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)