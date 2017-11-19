---
title: "IDebugThreadCall 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall 介面
`IDebugThreadCall`通常會實作介面的元件，與跨執行緒呼叫`IDebugThread`封送處理程序的偵錯管理員 (PDM) 所提供的實作。  
  
 PDM 呼叫`IDebugThreadCall`介面中所需的執行緒，而`IDebugThreadCall`介面會分派的呼叫所需的實作。 `IDebugThreadCall`介面會轉換為參數傳遞至適當的頂端的參數資訊。  
  
 `IDebugThreadCall`介面是無限制執行緒的物件。  
  
## <a name="methods"></a>方法  
 除了繼承自`IUnknown`、`IDebugThreadCall`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|如何處理到另一個執行緒中執行程式碼呼叫。|