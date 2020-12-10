---
title: 撰寫 Common Language Runtime 運算式評估工具 |Microsoft Docs
description: 瞭解如何撰寫 common language runtime 的運算式評估工具，以評估正在進行程式碼語言中的運算式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1674ae8345873ede5d1b4afb04774d6ed0469b4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996314"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>撰寫 common language runtime 運算式評估工具
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 運算式評估工具 (EE) 是 debug 引擎的一部分 (DE) ，它會處理產生要進行偵錯工具代碼之程式設計語言的語法和語義。 運算式必須在程式設計語言的內容中進行評估。 例如，在某些語言中，"A + B" 運算式表示「A 和 B 的總和」。 在其他語言中，相同的運算式可能表示「A 或 B」。 因此，必須針對每個程式設計語言撰寫個別的 EE，以產生要在 Visual Studio IDE 中進行調試的物件程式碼。

 Visual Studio debug 封裝的某些層面必須在程式設計語言的內容中解讀程式碼。 例如，當執行在中斷點停止時，必須評估並顯示使用者已在 **監看** 式視窗中輸入的任何運算式。 使用者可以在 [ **監看** 式] 視窗 **或 [即時** 運算] 視窗中輸入運算式，以變更區域變數的值。

## <a name="in-this-section"></a>本節內容
 [Common language runtime 和運算式評估](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) 說明當您將專屬程式設計語言整合至 Visual Studio IDE 時，撰寫可在專屬語言內容中評估運算式的 EE，可讓您編譯成 Microsoft 中繼語言 (MSIL) ，而不需要撰寫 debug engine。

 [運算式評估工具架構](../../extensibility/debugger/expression-evaluator-architecture.md) 討論如何執行所需的 EE 介面，以及如何 (SP) 和系結器介面呼叫 common language runtime 符號提供者。

 [註冊運算式評估](../../extensibility/debugger/registering-an-expression-evaluator.md) 工具請注意，EE 必須將本身註冊為具有 common language runtime 和 Visual Studio 執行時間環境的 class factory。

 [執行運算式評估](../../extensibility/debugger/implementing-an-expression-evaluator.md) 工具描述評估運算式的程式如何包括 debug engine (DE) 、符號提供者 (SP) 、系結器物件，以及運算式評估工具 (EE) 。

 [顯示區域變數](../../extensibility/debugger/displaying-locals.md) 描述當執行暫停時，debug 封裝會呼叫 DE 來取得區域變數和引數的清單。

 [評估監看式視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md) 記錄 Visual Studio debug 封裝如何呼叫 DE 來判斷其監看清單中每個運算式的目前值。

 [變更本機的值](../../extensibility/debugger/changing-the-value-of-a-local.md) 說明在變更本機的值時，[區域變數] 視窗中的每一行都有相關聯的物件，可提供本機的名稱、類型和目前的值。

 [執行型別視覺化和自訂查看](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) 器說明哪些介面需要由哪個元件所執行，以支援類型視覺化程式和自訂檢視器。

## <a name="see-also"></a>另請參閱
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
