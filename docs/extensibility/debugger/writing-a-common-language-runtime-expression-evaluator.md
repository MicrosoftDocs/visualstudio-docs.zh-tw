---
title: 撰寫 Common Language Runtime 運算式評估工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c295fcd881ed5348842355846c37af95b725f17e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348238"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>撰寫 common language runtime 運算式評估工具
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 運算式評估工具 (EE) 是偵錯引擎 (DE) 處理語法的一部分，並產生程式碼進行偵錯的程式語言的語意。 運算式必須評估內容中的一種程式設計語言。 比方說，在某些語言中，"A + B"的運算式表示"總和 A 和 b。 」 在其他語言中，相同的運算式可能表示 「 A 或 B 」 因此，個別 EE 必須寫入針對每個 Visual Studio IDE 中產生物件来進行偵錯的程式碼的程式設計語言。

 Visual Studio 偵錯封裝的某些層面必須解譯的程式設計語言的內容中的程式碼。 比方說，當執行暫止於中斷點時，任何使用者已輸入的運算式**監看式**必須評估並顯示視窗。 使用者可以變更本機變數的值輸入到運算式**監看式** 視窗或 into**即時運算**視窗。

## <a name="in-this-section"></a>本節內容
 [Common language runtime 和運算式評估](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)說明，您會將專屬的程式語言整合到 Visual Studio IDE，撰寫 EE 能夠評估的專屬語言的運算式內容中時可讓您編譯成 Microsoft intermediate language (MSIL)，而不需要撰寫偵錯引擎。

 [運算式評估工具架構](../../extensibility/debugger/expression-evaluator-architecture.md)討論如何實作必要的 EE 介面和呼叫的通用語言執行階段的符號提供者 (SP) 和繫結器介面。

 [註冊運算式評估工具](../../extensibility/debugger/registering-an-expression-evaluator.md)EE 必須註冊本身做為通用語言執行平台和 Visual Studio 執行階段環境的 class factory 的資訊。

 [實作運算式評估工具](../../extensibility/debugger/implementing-an-expression-evaluator.md)將告訴您如何評估運算式的程序包含偵錯引擎 (DE)、 符號提供者 (SP)、 繫結器物件和運算式評估工具 (EE)。

 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)將告訴您如何，當執行暫停時，偵錯封裝呼叫 DE，若要取得的本機變數和引數清單。

 [評估監看式視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)文件 Visual Studio 偵錯套件如何呼叫 DE，以判斷其監看清單中的每個運算式的目前值。

 [變更區域變數的值](../../extensibility/debugger/changing-the-value-of-a-local.md)說明變更區域變數的值，[區域變數] 視窗的每一行有相關聯的物件，提供名稱、 類型和區域變數的目前值。

 [實作類型視覺化檢視和自訂檢視器](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)說明哪些介面需要實作所支援類型視覺化檢視和自訂檢視器的元件。

## <a name="see-also"></a>另請參閱
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)