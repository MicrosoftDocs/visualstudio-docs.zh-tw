---
title: 傳送事件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125750"
---
# <a name="sending-events"></a>傳送事件
偵錯工具與偵錯引擎 (DE) 之間的通訊機制是 DCOM 所根據的事件模型。 事件會傳送為 COM 物件，且每個事件都有指定下列參數：  
  
-   呼叫事件 DE。  
  
-   發生什麼情況的描述。  
  
-   處理程序、 程式和執行緒的資訊來識別的事件發生所在的內容。 處理程序不會傳送事件從 DE 傳送。  
  
-   指出事件是否為同步或非同步事件類型。  
  
 使用方法傳送所有的偵錯事件[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [事件來源](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 說明兩個來源的事件： 偵錯引擎 (DE) 工作階段偵錯和管理員 (SDM)。  
  
 [支援的事件類型](../../extensibility/debugger/supported-event-types.md)  
 討論目前支援的事件類型： 非同步和同步。  
  
 [事件描述](../../extensibility/debugger/event-descriptions.md)  
 定義事件和其使用的原因。  
  
## <a name="related-sections"></a>相關章節  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 說明將 DE 直譯器或作業系統，來提供偵錯服務的運作方式。