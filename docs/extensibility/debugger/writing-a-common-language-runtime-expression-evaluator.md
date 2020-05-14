---
title: 編寫通用語言運行時運算式賦值器 |微軟文件
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
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712316"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>編寫通用語言執行時表示式賦值器
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 運算式賦值器 (EE) 是除錯引擎 (DE) 的一部分,用於處理生成要調試的程式碼的程式設計語言的語法和語義。 表達式必須在程式設計語言的上下文中計算。 例如,在某些語言中,表達式"A+B"表示"A 和B的總和"。 在其他語言中,相同的表達式可能表示"A 或 B"。 因此,必須為生成要在 Visual Studio IDE 中調試的對象代碼的每個程式設計語言編寫單獨的 EE。

 Visual Studio 調試包的某些方面必須在程式設計語言的上下文中解釋代碼。 例如,當執行在斷點停止時,必須計算並顯示使用者鍵入到**Watch**視窗中的任何表達式。 使用者可以通過在 **「監視」** 視窗或 **「立即」** 視窗中鍵入表達式來更改本地變數的值。

## <a name="in-this-section"></a>本節內容
 [通用語言執行時與表示式運算](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)說明在將專有程式設計語言整合到 Visual Studio IDE 中時,撰寫能夠評估專有語言上下文中運算式 EE 允許您編譯到 Microsoft 中間語言 (MSIL),而無需編寫調試引擎。

 [運算式賦值器架構結構](../../extensibility/debugger/expression-evaluator-architecture.md)討論如何實現所需的 EE 介面並呼叫通用語言執行時符號提供者 (SP) 和黏合劑介面。

 [註冊運算式賦值器](../../extensibility/debugger/registering-an-expression-evaluator.md)請注意,EE 必須將自己註冊為具有通用語言運行時和 Visual Studio 運行時環境的類工廠。

 [實作式賦值器](../../extensibility/debugger/implementing-an-expression-evaluator.md)描述計算表示式的過程如何包括除錯引擎 (DE)、符號提供者 (SP)、活頁器物件和運算式賦值器 (EE)。

 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)描述除錯套件在執行暫停時如何呼叫 DE 來獲取本地變數和參數的清單。

 [監控監視視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)記錄 Visual Studio 除錯套件如何呼叫 DE 以確定其監視清單中每個表示式的當前值。

 [變更本地值](../../extensibility/debugger/changing-the-value-of-a-local.md)說明在更改局部變數的值時,「局部變數」視窗的每一行都有一個關聯的物件,該物件提供本地的名稱、類型和當前值。

 [實現類型視覺化器和自訂檢視器](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)說明需要由哪個元件實現哪個介面來支援類型可視化器和自定義查看器。

## <a name="see-also"></a>另請參閱
 [視覺化工作室除錯器可擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
