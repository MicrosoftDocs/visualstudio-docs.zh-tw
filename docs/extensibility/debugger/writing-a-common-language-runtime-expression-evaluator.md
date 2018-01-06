---
title: "撰寫通用語言執行階段運算式評估工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d52a9dbed6cec64426247a0b92bff2b8ec98ec97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>撰寫通用語言執行階段運算式評估工具
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 偵錯引擎 (DE) 處理語法的一部分而產生的程式碼進行偵錯的程式語言的語意，運算式評估工具 (EE)。 運算式必須評估內容中的程式語言。 比方說，在某些語言中，"A + B"的運算式表示"總和 A 和 B 」 在其他語言中，相同的運算式可能表示 「 A 或 B 」。 因此，個別 EE 必須撰寫會產生物件程式碼進行偵錯，Visual Studio IDE 中的每種程式設計語言。  
  
 Visual Studio 偵錯封裝的某些方面必須解譯的程式語言的內容中的程式碼。 例如，當停止執行在中斷點時，使用者已輸入的任何運算式**監看式**必須評估並顯示視窗。 此外，使用者可以變更本機變數的值輸入到運算式**監看式**視窗或**即時運算**視窗。  
  
## <a name="in-this-section"></a>本節內容  
 [Common Language Runtime 和運算式評估](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 說明，當您要將專屬的程式語言整合到 Visual Studio IDE 中，撰寫 EE 能夠評估內容中的專用語言的運算式可讓您編譯成 Microsoft intermediate language (MSIL)不需要撰寫偵錯引擎。  
  
 [運算式評估工具架構](../../extensibility/debugger/expression-evaluator-architecture.md)  
 討論如何實作所需的 EE 介面和呼叫的通用語言執行階段的符號提供者 (SP) 和繫結器介面。  
  
 [註冊運算式評估工具](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 附註 EE 必須註冊本身做為與通用語言執行平台和 Visual Studio 執行階段環境的 class factory。  
  
 [實作運算式評估工具](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 描述如何評估運算式的程序包括偵錯引擎 (DE)、 符號提供者 (SP)、 繫結器物件，以及運算式評估工具 (EE)。  
  
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)  
 描述如何，暫停執行，當偵錯封裝呼叫 DE，若要取得的本機變數和引數清單。  
  
 [評估監看式視窗的運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 文件 [Visual Studio 偵錯封裝如何呼叫 DE，以判斷其監看清單] 中的每個運算式的目前值。  
  
 [變更區域變數的值](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 說明中的本機值變更，[區域變數] 視窗的每一行有相關聯的物件，提供名稱、 類型和目前的本機值。  
  
 [實作類型視覺化檢視和自訂檢視器](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 說明哪些介面必須實作以支援類型的視覺化檢視和自訂檢視器的元件。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)