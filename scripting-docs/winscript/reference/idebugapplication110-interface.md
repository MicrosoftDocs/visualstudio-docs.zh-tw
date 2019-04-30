---
title: IDebugApplication110 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0991f27077cf3ac3eb5cbfdcbb409fd5903d9a66
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446384"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 介面
`IDebugApplication110`介面會擴充功能[IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)。 您可以取得此介面的執行個體的實作上呼叫 QueryInterface [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)。  
  
> [!IMPORTANT]
> 這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugApplication110` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|在主執行緒上進行同步呼叫。|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|在主執行緒上進行非同步呼叫。|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|等候任何一個指定的控制代碼接收信號，同時允許跨執行緒呼叫張貼到此對話。 從偵錯工具的執行緒，就必須呼叫這個方法。|