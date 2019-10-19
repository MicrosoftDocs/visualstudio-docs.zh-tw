---
title: IDebugApplicationThread110：： IsThreadCallable |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ff81190247454a4471a4150843d3fb0aaed5999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574472"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
判斷這個執行緒是否處於會處理使用 PDM 執行緒切換機制（例如 SynchronousCallInThread）所進行之呼叫的狀態。  
  
> [!IMPORTANT]
> [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)是由 PDM 11.0 和更新版本所執行。 可在 activdbg100.h 中找到。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>參數  
 `pfIsCallable`  
 [out] `true` 如果執行緒可呼叫，則為，否則為 `false`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugApplicationThread110 介面](../../winscript/reference/idebugapplicationthread110-interface.md)