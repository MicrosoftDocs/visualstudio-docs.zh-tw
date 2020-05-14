---
title: 傳送事件 |微軟文件
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
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713034"
---
# <a name="send-events"></a>傳送事件
除錯器和除錯引擎 (DE) 之間的通訊機制是基於 DCOM 的事件模型。 事件作為 COM 物件傳送,每個事件都有指定:

- 調用事件的 DE。

- 所發生的事情的描述。

- 標識事件發生地上下文的進程、程序和線程資訊。 不會為從 DE 發送的事件發送進程。

- 指示事件是同步事件還是異步的事件類型。

  所有調試事件都使用[IDebugEvent回調2::事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送。

## <a name="in-this-section"></a>本節內容
 [事件來源](../../extensibility/debugger/event-sources-visual-studio-sdk.md)解釋兩個事件源:調試引擎 (DE) 和會話調試管理器 (SDM)。

 [受支援的事件型態](../../extensibility/debugger/supported-event-types.md)討論當前支援的事件類型:非同步和同步。

 [事件描述](../../extensibility/debugger/event-descriptions.md)定義事件及其使用原因。

## <a name="related-sections"></a>相關章節
 [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)描述 DE 如何與解釋器或作業系統一起提供調試服務。
