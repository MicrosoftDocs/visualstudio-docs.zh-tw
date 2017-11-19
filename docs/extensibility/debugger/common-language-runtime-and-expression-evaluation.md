---
title: "Common Language Runtime 和運算式評估 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba9a9a6b406ad5a94cced7820e6b4581db56eb2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime 和運算式評估
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 編譯器，例如 Visual Basic 和 C# （唸成 c-sharp），以 Common Language Runtime (CLR) 為目標，產生 Microsoft Intermediate Language (MSIL)，這是更新版本編譯為原生程式碼。 CLR 提供偵錯引擎 (DE) 產生的程式碼進行偵錯。 如果您打算將您專屬的程式語言整合到 Visual Studio IDE，您可以選擇要編譯為 MSIL，並因此不會寫入您自己 DE。 不過，您必須撰寫能夠評估您的程式語言的內容中運算式的運算式評估工具 (EE)。  
  
## <a name="discussion"></a>討論  
 電腦語言運算式通常會產生一組資料物件和一組用來操作這些運算子剖析。 例如，"A + B"可能會剖析加法運算子 （+） 套用至資料的運算式的物件"A"和"B、"但可能會造成另一個資料物件。 程式通常會表示資料物件、 運算子和其關聯的一整組為樹狀結構，在樹狀結構節點的運算子與分支的資料物件。 具有已細分成樹狀目錄格式的運算式通常稱為剖析樹狀結構。  
  
 一旦已剖析運算式，呼叫的符號提供者 (SP)，以評估每個資料物件。 例如，如果"A"定義在一個以上的方法，則問題"哪些 A？" 必須在解答之前可以確定 A 的值。 預存程序所傳回的回應是類似 「 第五個堆疊框架上第三個項目 」 或者 「 靜態記憶體開頭超過 50 個位元組的配置給這個方法 」。  
  
 除了產生 MSIL 的程式本身，CLR 編譯器也會產生非常描述性寫入程式資料庫 (.pdb) 檔案的偵錯資訊。 只要專屬語言編譯器會產生與 CLR 編譯器相同的格式中偵錯資訊，在 CLR 預存程序是無法識別語言的具名資料物件。 一旦已經識別為具名的資料物件，EE 使用繫結器物件產生關聯 （或繫結） 的資料物件會保留該物件的值之記憶體區域。 DE 然後來取得或設定資料物件的新值。  
  
 專屬的編譯器可以提供 CLR 偵錯資訊，藉由呼叫`ISymbolWriter`介面 (在.NET Framework 命名空間中定義的所在`System.Diagnostics.SymbolStore`)。 專屬的編譯器編譯為 MSIL，並寫入偵錯資訊，透過這些介面，可以使用 CLR DE 和 SP 這可大幅簡化了將專用語言整合到 Visual Studio IDE。  
  
 當 CLR DE 呼叫專屬的 EE 評估運算式時，DE 提供 EE 預存程序和繫結器物件的介面。 因此，撰寫 CLR 為基礎的偵錯引擎表示它是為了只實作適當的運算式評估工具的介面。CLR 會負責繫結和處理您的符號。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)