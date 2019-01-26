---
title: 語言服務支援偵錯 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ebb0293e17fe022fc04c9e4e6724fa49a8c3056
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994221"
---
# <a name="language-service-support-for-debugging"></a>語言服務支援偵錯
語言服務可以提供功能，可支援偵錯工具透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>介面。 這些功能包括驗證中斷點，並提供運算式，以一份**自動變數**視窗。  
  
 不過，您需要有偵錯您的語言的運算式評估工具。 運算式評估工具會負責評估運算式，以產生偵錯時的值。 如需實作 CLR 運算式評估工具的資訊，請參閱：  
  
-   [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Managed 的運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>編譯器輸出  
 編譯器的型別會決定您要如何實作您的語言偵錯。 如果您的編譯器的 Windows 作業系統為目標，並寫入.pdb 檔案，您可以使用原生程式碼偵錯引擎，可整合至 Visual Studio 偵錯程式。 如果您的編譯器會產生 Microsoft intermediate language (MSIL)，您可以使用 managed 程式碼偵錯引擎，它也會整合到 Visual Studio 偵錯程式。 如果編譯器以目標專用的作業系統或不同的執行階段環境，您要撰寫您自己的偵錯引擎。  
  
 如需有關如何實作您的語言偵錯的詳細資訊，請參閱[開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)Visual Studio 偵錯 」 的 sdk。