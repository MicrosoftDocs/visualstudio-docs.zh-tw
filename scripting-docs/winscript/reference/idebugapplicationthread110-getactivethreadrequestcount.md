---
title: IDebugApplicationThread110：： GetActiveThreadRequestCount |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574482"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
傳回目前正在處理之 PDM 執行緒切換機制的執行緒要求數目。 這個數位通常是0或1。 不過，如果一個執行緒呼叫開始處理，但觸發執行緒的同步呼叫，或是暫停執行緒，並允許重新處理連入呼叫（例如，藉由觸發 IRemoteDebugApplicationEvents，則此數目可能會較高） [介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)事件，在偵錯工具執行緒上發出）。  
  
> [!IMPORTANT]
> [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>參數  
 `puiThreadRequests`  
 脫銷執行緒要求的數目。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)