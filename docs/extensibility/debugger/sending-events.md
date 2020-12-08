---
title: 傳送事件 |Microsoft Docs
description: 瞭解偵錯工具和偵測引擎如何使用以 DCOM 為基礎的事件模型。 事件會以 COM 物件的形式傳送。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0262868ae442bfdd8b99c16f59e000f4ebfc35c5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847906"
---
# <a name="send-events"></a>傳送事件
偵錯工具與 debug engine (DE) 之間的通訊機制是以 DCOM 為基礎的事件模型。 事件會以 COM 物件的形式傳送，且每個事件都有參數，可指定：

- 呼叫事件的 DE。

- 發生狀況的描述。

- 處理常式、程式和執行緒資訊，識別發生事件的位置。 不會傳送從 DE 傳送的事件的進程。

- 表示事件為同步或非同步事件種類。

  所有的 debug 事件都是使用方法 [IDebugEventCallback2：： Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)來傳送。

## <a name="in-this-section"></a>本節內容
 [事件來源](../../extensibility/debugger/event-sources-visual-studio-sdk.md) 說明兩個事件來源： debug engine (DE) ，以及會話 debug manager (SDM) 。

 [支援的事件種類](../../extensibility/debugger/supported-event-types.md) 討論目前支援的事件種類：非同步和同步。

 [事件描述](../../extensibility/debugger/event-descriptions.md) 定義事件及其使用的原因。

## <a name="related-sections"></a>相關章節
 [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md) 描述 DE 如何搭配解譯器或作業系統來提供偵錯工具。
