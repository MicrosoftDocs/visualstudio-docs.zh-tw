---
title: Common Language Runtime 和運算式評估 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fb29119fd0598547925cad5ca82ab40ab693a07
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941383"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime 和運算式評估
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 編譯器，例如 Visual Basic 和 C# （唸成 c-sharp），以 Common Language Runtime (CLR) 為目標，產生 Microsoft Intermediate Language (MSIL)，也就是更新版本編譯為原生程式碼。 CLR 提供偵錯引擎 (DE) 產生的程式碼偵錯。 如果您打算將您專屬的程式語言整合到 Visual Studio IDE，您可以選擇 編譯為 MSIL，並因此將不需要撰寫您自己的裝置。 不過，您必須撰寫能夠評估您的程式語言的內容中運算式的運算式評估工具 (EE)。  
  
## <a name="discussion"></a>討論  
 電腦語言的運算式通常會產生一組資料物件和一組用來操作這些運算子進行剖析。 例如，"A + B"可能要套用加法運算子 （+） 剖析資料的運算式物件"A"和"B、"可能會產生另一個資料物件。 在程式中最常表示的整組資料物件、 運算子和其關聯為樹狀結構，在節點樹狀結構的運算子與分支的資料物件。 具有已細分成樹狀結構形式的運算式通常稱為剖析樹狀結構。  
  
 一旦已剖析運算式，會呼叫的符號提供者 (SP) 可評估每個資料物件。 例如，如果在一個以上的方法，則問題中都已定義的"A""的 A？" 必須回答才能確定的值。 預存程序所傳回的答案是類似 「 第五個堆疊框架上第三個項目 」 或者 「 超過開頭的靜態記憶體的 50 個位元組的配置給這個方法 」。  
  
 除了產生 MSIL 的程式本身，CLR 編譯器也會產生相當的描述性寫入程式資料庫 (.pdb) 檔案的偵錯資訊。 只要專屬語言編譯器會產生與 CLR 編譯器相同的格式中的偵錯資訊，在 CLR 預存程序是無法識別語言的具名資料物件。 一旦已識別的具名的資料物件，EE 使用繫結器物件建立關聯 （或繫結） 的資料物件會保留該物件的值之記憶體區域。 DE 然後可以取得或設定新的資料物件的值。  
  
 專利的編譯器可以提供偵錯資訊，藉由呼叫的 CLR`ISymbolWriter`介面 (定義於.NET Framework 命名空間中`System.Diagnostics.SymbolStore`)。 專利的編譯器編譯為 MSIL，並寫入偵錯資訊，透過這些介面，可以使用 CLR DE 和 SP 這可大幅簡化將專屬的語言整合到 Visual Studio IDE。  
  
 當 CLR DE 呼叫專屬的 EE 評估運算式時，DE 提供 EE 包含預存程序和繫結器物件的介面。 因此，撰寫 CLR 為基礎的偵錯引擎表示它則只需要實作適當的運算式評估工具的介面;CLR 會負責繫結和處理您的符號。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
