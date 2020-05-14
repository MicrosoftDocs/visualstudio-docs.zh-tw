---
title: 斷點(可視化工作室 SDK) |微軟文件
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
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739199"
---
# <a name="breakpoints-visual-studio-sdk"></a>中斷點 (Visual Studio SDK)
有三種類型的斷點:掛起、綁定和錯誤。

 **暫停的斷點:**

- 是一個抽象,它包含將斷點綁定到一個或多個程式中的一個或多個代碼上下文所需的所有資訊。 每次調試程式會導致代碼載入時,調試引擎都會檢查所有掛起的斷點,以查看是否可以綁定它們。

   掛起的斷點本身從不綁定到代碼,而是收集並據說包含它生成的所有綁定斷點。

- 由[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面表示。

  **繫結斷點:**

- 是與單個程式碼上下文關聯或綁定到單個程式碼上下文的斷點的抽象。 每個綁定斷點都是為了回應掛起的斷點而生成的。 但是,掛起的斷點可以生成多個綁定斷點。

   卸載代碼時,可以取消綁定斷點並丟棄綁定斷點。

- 由[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面表示。

  **錯誤斷點:**

- 是描述嘗試將掛起的斷點綁定到代碼上下文時的錯誤的抽象。 錯誤斷點描述位置或斷點運算式本身的錯誤。 有關詳細資訊,請參閱[綁定斷點](../../extensibility/debugger/binding-breakpoints.md)。

   斷點錯誤可以是錯誤或警告。

- 由[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面表示。

## <a name="see-also"></a>另請參閱
- [Programs](../../extensibility/debugger/programs.md)
- [除錯器概念](../../extensibility/debugger/debugger-concepts.md)
- [代碼內容](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
