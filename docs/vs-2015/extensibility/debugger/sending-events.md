---
title: 傳送事件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65c86cb8028d5c310de6f48c753d862865ea7a46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497986"
---
# <a name="sending-events"></a>傳送事件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[傳送事件](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-events)。  
  
偵錯工具與偵錯引擎 (DE) 之間的通訊機制是 DCOM 所根據的事件模型。 事件會傳送為 COM 物件，以及每個事件都指定下列參數：  
  
-   呼叫事件 DE。  
  
-   描述發生什麼事。  
  
-   處理程序、 方案，以及識別發生事件的內容的執行緒資訊。 此程序不會傳送規定所傳來的事件。  
  
-   事件類型，指出事件是否為同步或非同步。  
  
 使用方法傳送所有的偵錯事件[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [事件來源](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 說明兩個來源的事件： 偵錯引擎 (DE) 和工作階段進行偵錯管理員 (SDM)。  
  
 [支援的事件類型](../../extensibility/debugger/supported-event-types.md)  
 討論目前支援的事件類型： 非同步和同步。  
  
 [事件描述](../../extensibility/debugger/event-descriptions.md)  
 定義事件和其使用的原因。  
  
## <a name="related-sections"></a>相關章節  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 說明 DE 解譯器或作業系統，提供偵錯服務的運作方式。

