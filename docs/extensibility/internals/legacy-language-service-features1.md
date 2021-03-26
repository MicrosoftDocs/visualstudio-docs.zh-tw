---
title: 舊版語言服務功能 1 |Microsoft Docs
description: 瞭解受管理套件架構 (的 Visual Studio 功能) 語言服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2bb5169eeb53aa16d0827cdf50cb50d0db34d996
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074509"
---
# <a name="legacy-language-service-features-1"></a>舊版語言服務功能1
受控封裝架構 (MPF) 語言服務可支援一或多個 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 功能，例如語法醒目提示、IntelliSense 和中斷點驗證。 每項功能都可以獨立執行，但除了語法醒目提示以外，只需要掃描器，但全部都需要剖析器和掃描器。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 描述支援語言組比對（也稱為大括弧比對）所需的條件。

- [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 描述支援對所選程式碼加上批註和取消批註所需的內容。

- [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 描述支援內嵌于原始程式檔中的檔案屬性所需的內容。

- [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 描述透過執行隱藏區域來支援大綱所需的內容。

- [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 描述支援重新格式化程式碼所需的內容。

- [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 描述支援程式碼片段所需的功能，這是插入並可編輯的程式碼區段。

- [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 描述支援 IntelliSense 參數資訊作業，以在輸入方法時顯示方法簽章所需的內容。

- [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 描述支援 IntelliSense 快速諮詢作業來顯示識別碼相關資訊所需的內容。

- [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 描述支援 IntelliSense 成員完成作業，以從清單中選取命名空間成員所需的內容。

- [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 描述支援 IntelliSense 完成文字作業以完成部分具類型字的必要動作。

- [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 描述當您進行調試時，語言服務可如何 **支援 [自動** 變數] 視窗。

- [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 描述如何使用編輯器視圖頂端的 **導覽** 列，以提供在該視圖所顯示檔案中的任何類型或成員的快速導覽。

- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 描述支援原始程式碼語法醒目提示所需的內容。

- [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 描述語言服務可在偵錯工具之外支援驗證中斷點的功能。

## <a name="related-sections"></a>相關章節
- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 描述必須要有哪些剖析器和掃描器，才能執行使用 managed package framework 之語言服務的所有功能。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 描述使用 MPF 來執行語言服務所需的內容。

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)

 描述向註冊以 MPF 為基礎之語言服務的必要步驟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [使用 IntelliSense](../../ide/using-intellisense.md)

 說明 IntelliSense 讓語言參考易於存取的方式。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 提供有關如何使用 managed package framework (MPF) 在 managed 程式碼中執行功能完整的語言服務的資訊。
