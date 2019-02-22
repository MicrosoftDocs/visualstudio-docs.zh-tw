---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs
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
ms.openlocfilehash: 8bd776aedd4df61797419795afb8dcc8afeb9318
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348179"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
從 PDM 的執行緒切換目前正在處理的機制，會傳回執行緒的要求數目。 這個數字通常是 0 或 1。 不過，如果一個執行緒呼叫開始處理，但同步呼叫的執行緒，從觸發程序或否則暫止的執行緒，也允許再次處理傳入的呼叫數目可能會更高 (例如，透過觸發[IRemoteDebugApplicationEvents 介面](../../winscript/reference/iremotedebugapplicationevents-interface.md)偵錯工具執行緒發出的事件)。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)是實作由 PDM v11.0 和更新版本。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>參數  
 `puiThreadRequests`  
 [out]執行緒要求的數目。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)