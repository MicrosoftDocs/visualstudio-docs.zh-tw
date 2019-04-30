---
title: IDebugThreadCall 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004867"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall 介面
`IDebugThreadCall`通常會實作介面的元件，可使用的跨執行緒呼叫`IDebugThread`封送處理程序的偵錯管理員 (PDM) 所提供的實作。  
  
 PDM 呼叫`IDebugThreadCall`介面中所需的執行緒，而`IDebugThreadCall`介面分派的呼叫所需的實作。 `IDebugThreadCall`介面會轉換為參數傳遞至適當的頂端的參數資訊。  
  
 `IDebugThreadCall`介面是無限制執行緒的物件。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IDebugThreadCall`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|處理在另一個執行緒中執行程式碼的呼叫。|