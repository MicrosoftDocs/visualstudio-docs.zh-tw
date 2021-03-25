---
title: Visual Studio 偵錯工具擴充性 |Microsoft Docs
description: 本文描述 Visual Studio 偵錯工具擴充性，並提供 Visual Studio 偵錯工具的相關文章連結。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbc44da3f98555774dd62c2b061bbf3a0799926e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057724"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio 偵錯工具擴充性
Visual Studio 包含完全互動式的原始程式碼偵錯工具，可提供功能強大且容易使用的工具來追蹤程式中的 bug。 偵錯工具具有 Visual Basic、c #、C/c + + 和 JavaScript 的完整支援。 不過，使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 可從 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=21835)取得的，可在偵錯工具中支援其他程式設計語言，且具有相同的豐富功能。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具是常見的前端 (也就是，使用者介面會) 至偵錯工具，而這些元件則會依所要進行的語言而異。 針對新的語言，偵錯工具所需的一切都必須 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建立必要的後端元件，例如 debug engine (DE) 。 這就是進入的位置 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 。

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]包含 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建立新的 DE 時所需之所有元素的完整參考。 此外，還有一些範例和教學課程可協助您開始著手。

 如需具有偵錯工具支援之語言專案系統的完整範例，請參閱 [IronPython 範例](https://www.microsoft.com/download/details.aspx?id=55984)。

 下列各節描述如何使用擴充偵錯工具 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 。

## <a name="in-this-section"></a>本節內容
 [開始](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) 使用說明什麼是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 調試提供的，以及如何安裝 SDK。

 [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md) 記載自訂的 DE 流程，從準備您的程式到取消卸離。

 [撰寫 CLR 運算式評估](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 工具說明您是否必須撰寫運算式評估工具。

 [選擇 debug engine 執行策略](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) 討論如何執行您的 DE。

 [參考](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) 記錄 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 調試 API。

 [範例](../../extensibility/debugger/visual-studio-debugging-samples.md) 包含通用語言運行時程表達式評估工具範例和 debug engine 範例的連結。
