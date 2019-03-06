---
title: 傳送事件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd282dd38d322a5b7d9821406d30a303fabb02bb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685062"
---
# <a name="send-events"></a>傳送事件
偵錯工具與偵錯引擎 (DE) 之間的通訊機制是 DCOM 所根據的事件模型。 事件會傳送為 COM 物件，且每個事件具有指定的參數：

- 呼叫事件 DE。

- 描述發生什麼事。

- 處理程序、 方案，以及識別發生事件的內容的執行緒資訊。 此程序不會傳送規定所傳來的事件。

- 事件類型，指出事件是否為同步或非同步。

  使用方法傳送所有的偵錯事件[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)。

## <a name="in-this-section"></a>本節內容
 [事件來源](../../extensibility/debugger/event-sources-visual-studio-sdk.md)說明兩個來源的事件： 偵錯引擎 (DE) 和工作階段進行偵錯管理員 (SDM)。

 [支援的事件類型](../../extensibility/debugger/supported-event-types.md)討論目前支援的事件類型： 非同步和同步。

 [事件描述](../../extensibility/debugger/event-descriptions.md)定義事件和其使用的原因。

## <a name="related-sections"></a>相關章節
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)說明 DE 解譯器或作業系統，提供偵錯服務的運作方式。