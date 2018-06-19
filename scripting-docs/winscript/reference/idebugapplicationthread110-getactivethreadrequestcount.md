---
title: IDebugApplicationThread110::GetActiveThreadRequestCount |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fb4d19bb77a4380c3c0a04f7e7808b82ca3f6ae4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726278"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
傳回執行緒要求的數目從 PDM 執行緒切換目前正在處理的機制。 這個號碼通常是 0 或 1。 不過，如果一個執行緒呼叫開始處理，但觸發同步呼叫出執行緒，否則將執行緒暫止並允許對再次處理連入呼叫數目可能很高 (例如，透過觸發[IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)事件，這在偵錯工具執行緒上發出)。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)會實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>參數  
 `puiThreadRequests`  
 [out]執行緒要求的數目。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)