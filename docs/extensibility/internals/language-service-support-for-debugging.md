---
title: 語言服務對除錯的支援 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707440"
---
# <a name="language-service-support-for-debugging"></a>語言服務支援偵錯
語言服務可以提供透過介面支援除錯器的功能<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>。 這些功能包括驗證斷點和向 **「自動」** 視窗提供運算式清單。

 但是,您需要有一個表達式賦值器來調試您的語言。 表達式賦值器負責在調試時評估表達式以生成值。 有關實現 CLR 運算式賦值器的資訊,請參閱:

- [CLR 運算式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [託管運算器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>編譯器輸出
 編譯器類型確定需要執行哪些操作來實現語言的調試。 如果編譯器以 Windows 作業系統為目標並編寫 .pdb 檔,則可以使用整合到 Visual Studio 的本機代碼調試引擎來調試程式。 如果編譯器生成 Microsoft 中間語言 (MSIL),則可以使用託管代碼調試引擎調試程式,該引擎也將集成到 Visual Studio 中。 如果編譯器以專有操作系統或不同的運行時環境為目標,則需要編寫自己的調試引擎。

 有關實現語言調試的詳細資訊,請參閱在可視化工作室調試 SDK 中[入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)。
