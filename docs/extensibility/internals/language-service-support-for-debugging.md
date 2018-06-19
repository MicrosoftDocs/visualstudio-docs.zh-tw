---
title: 語言服務支援偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59c044f6ffc3f2cdf0749f0192f4b8fa458b00cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128647"
---
# <a name="language-service-support-for-debugging"></a>語言服務支援偵錯
語言服務可以提供功能，可支援透過偵錯工具<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>介面。 這些功能包括驗證中斷點，並提供一份運算式**自動變數**視窗。  
  
 不過，您需要有偵錯您的語言的運算式評估工具。 運算式評估工具會負責評估運算式，以產生偵錯時的值。 如需實作 CLR 運算式評估工具的資訊，請參閱：  
  
-   [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Managed 的運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>編譯器輸出  
 編譯器的類型決定您需要如何實作偵錯您的語言。 如果編譯器為目標的 Windows 作業系統，並將寫入.pdb 檔案，您可以使用原生程式碼偵錯引擎整合到 Visual Studio 偵錯程式。 編譯器會產生 Microsoft intermediate language (MSIL)，您可以使用 managed 程式碼偵錯引擎，也會整合至 Visual Studio 偵錯程式。 如果您的編譯器目標專用的作業系統或不同的執行階段環境，您要撰寫您自己的偵錯引擎。  
  
 如需實作您的語言偵錯的詳細資訊，請參閱[入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)Visual Studio 偵錯 SDK 中。