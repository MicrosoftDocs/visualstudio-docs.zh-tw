---
title: 適用于偵錯工具的語言服務支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707440"
---
# <a name="language-service-support-for-debugging"></a>語言服務支援偵錯
語言服務可以提供透過介面支援偵錯工具的功能 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> 。 這些功能包括驗證中斷點，以及 **在 [自動** 變數] 視窗中提供運算式清單。

 不過，您必須擁有運算式評估工具才能對您的語言進行偵錯工具。 運算式評估工具會負責評估運算式，以在進行偵錯工具時產生值。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱：

- [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>編譯器輸出
 編譯器的型別會決定您需要執行哪些動作來為您的語言執行偵錯工具。 如果您的編譯器以 Windows 作業系統為目標並寫入 .pdb 檔案，您可以使用整合至 Visual Studio 的機器碼偵測引擎來將程式進行偵錯工具。 如果您的編譯器產生 Microsoft 中繼語言 (MSIL) ，您可以使用 managed 程式碼偵錯工具引擎（也整合至 Visual Studio）來將程式進行偵錯工具。 如果您的編譯器以專屬的作業系統或不同的執行時間環境為目標，則必須撰寫自己的偵錯工具引擎。

 如需有關為您的語言執行偵錯工具的詳細資訊，請參閱 Visual Studio 偵錯工具 SDK 中的 [消費者入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) 。
