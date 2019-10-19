---
title: IRemoteDebugApplication110：： GetMainThread |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff99c43f633da8454eb5fa32463886877e06ed72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574125"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
傳回呼叫[SetSite](http://go.microsoft.com/fwlink/?LinkId=232439)之主機的主執行緒，否則會傳回 E_FAIL。  
  
> [!IMPORTANT]
> [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>參數  
 `ppThread`  
 脫銷主要[IRemoteDebugApplicationThread 介面](../../winscript/reference/iremotedebugapplicationthread-interface.md)。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 介面](../../winscript/reference/iremotedebugapplication110-interface.md)