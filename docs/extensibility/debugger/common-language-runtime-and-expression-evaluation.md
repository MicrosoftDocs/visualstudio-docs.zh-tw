---
title: Common Language Runtime 和運算式評估 |Microsoft Docs
description: 瞭解 Common Language Runtime 如何與 debug engine 互動，以及如何將專屬程式設計語言整合到 Visual Studio IDE 中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c120ac1da59ab86e9419bcb031af46f1b3d900
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914253"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common language runtime 和運算式評估
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 編譯器（例如 Visual Basic 和 c #)  (會以 Common Language Runtime (CLR) 為目標，並產生 Microsoft 中繼語言 (MSIL) ，稍後會編譯成機器碼。 CLR 會提供 debug engine (DE) 來對產生的程式碼進行 debug 錯。 如果您打算將專屬的程式設計語言整合至 Visual Studio IDE，您可以選擇編譯成 MSIL，因此不需要自行撰寫 DE。 不過，您必須撰寫 (EE) 的運算式評估工具，以便能夠在程式設計語言的內容中評估運算式。

## <a name="discussion"></a>討論
 通常會剖析電腦語言運算式來產生一組資料物件，以及一組用來操作這些物件的運算子。 例如，可能會剖析運算式 "A + B"，將加法運算子 (+) 套用至資料物件 "A" 和 "B"，可能導致另一個資料物件。 在程式中，資料物件、運算子及其關聯的總集合最常以樹狀結構表示，並在樹狀結構的節點和資料物件的資料物件中，提供運算子。 已細分為樹狀結構的運算式通常稱為剖析樹狀結構。

 一旦剖析運算式，就會呼叫 (SP) 的符號提供者來評估每個資料物件。 例如，如果 "A" 是在一個以上的方法中定義，則問題為 "A？" 必須先回答，才能確認的值。 SP 傳回的答案就像是「第五個堆疊框架上的第三個專案」或「在配置給這個方法的靜態記憶體開頭以外的50個位元組」。

 除了為程式本身產生 MSIL 之外，CLR 編譯器也可以產生非常描述性的偵錯工具，並將其寫入至程式資料庫 (*.pdb*) 檔。 只要專屬語言編譯器以與 CLR 編譯器相同的格式產生 debug 資訊，CLR 的 SP 就能夠識別該語言的命名資料物件。 一旦識別出已命名的資料物件，EE 就會使用系結器物件，將 (或系結) 資料物件關聯至保存該物件值的記憶體區域。 然後，DE 可以取得或設定資料物件的新值。

 專屬的編譯器可以藉由呼叫 `ISymbolWriter` (定義于命名空間) .NET Framework 中的介面，來提供 CLR 偵錯工具的資訊 `System.Diagnostics.SymbolStore` 。 藉由編譯至 MSIL 並透過這些介面寫入偵錯工具資訊，專屬的編譯器可以使用 CLR DE 和 SP。 這可大幅簡化將專屬語言整合到 Visual Studio IDE 中的工作。

 當 CLR DE 呼叫專屬的 EE 來評估運算式時，DE 會將具有介面的 EE 提供給 SP 和系結器物件。 因此，撰寫以 CLR 為基礎的 debug 引擎表示只需要執行適當的運算式評估工具介面，CLR 會為您處理系結和符號處理。

## <a name="see-also"></a>另請參閱
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
