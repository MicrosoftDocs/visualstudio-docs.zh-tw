---
title: " (Visual Studio SDK) 的中斷點 |Microsoft Docs"
description: 深入瞭解下列三種中斷點類型：暫止、已系結和錯誤。 本文列出用來執行這些類型的介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d266bb97b6d3086a8f5b74100f5821a5cfca3af
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914448"
---
# <a name="breakpoints-visual-studio-sdk"></a>中斷點 (Visual Studio SDK)
有三種類型的中斷點：暫止、已系結和錯誤。

 **暫止的中斷點：**

- 是一種抽象層，其中包含將中斷點系結至一或多個程式中的一個或多個程式碼內容時所需的所有資訊。 每次正在調試的程式導致程式碼載入時，debug engine 都會檢查所有暫止的中斷點，以查看是否可以系結它們。

   暫止中斷點本身永遠不會系結至程式碼，而是會收集並說出它所產生的所有系結中斷點。

- 是由 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 介面表示。

  **系結中斷點：**

- 是與或系結至單一程式碼內容之中斷點的抽象概念。 會產生每個系結中斷點，以回應暫止中斷點。 但是，暫止中斷點可以產生一個以上的系結中斷點。

   當卸載程式碼時，系結中斷點可以解除系結和捨棄。

- 是由 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 介面表示。

  **錯誤中斷點：**

- 是一個抽象概念，用來描述嘗試將暫止中斷點系結至程式碼內容時的錯誤。 錯誤中斷點描述位置或中斷點運算式本身的錯誤。 如需詳細資訊，請參閱系結 [中斷點](../../extensibility/debugger/binding-breakpoints.md)。

   中斷點錯誤可能是錯誤或警告。

- 是由 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 介面表示。

## <a name="see-also"></a>另請參閱
- [程式](../../extensibility/debugger/programs.md)
- [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)
- [程式碼內容](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
