---
title: "IDebugApplication110 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 介面
`IDebugApplication110`介面延伸功能的[IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)。 您可以取得此介面的執行個體的實作上呼叫 QueryInterface [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugApplication110` 介面公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|會在主執行緒上的同步呼叫。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|在主執行緒上進行非同步呼叫。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|等候任何指定的控制代碼，同時允許發出信號的跨執行緒呼叫張貼至這個執行緒。 必須呼叫這個方法，從 偵錯工具執行緒。|