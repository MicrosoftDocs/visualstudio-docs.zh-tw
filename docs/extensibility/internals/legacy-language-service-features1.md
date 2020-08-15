---
title: 舊版語言服務功能 1 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f2a4010529d3d9727ceb76d6a34f2cbc41b959
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238475"
---
# <a name="legacy-language-service-features-1"></a>舊版語言服務功能1
受管理的封裝架構 (MPF) 語言服務可支援一或多個 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 功能，例如語法反白顯示、IntelliSense 和中斷點驗證。 每項功能都可以獨立執行，但全都需要剖析器和掃描器，但語法醒目提示除外，這只需要掃描器。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 說明支援語言組比對所需的內容，也稱為括弧對稱。

- [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 描述支援所選程式碼的批註和取消批註所需的內容。

- [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 描述支援內嵌在原始程式檔中之文件屬性所需的內容。

- [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 說明在隱藏區域的執行中支援大綱所需的功能。

- [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 說明支援重新格式化程式碼所需的功能。

- [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 描述支援程式碼片段所需的功能，這是插入並可編輯的程式碼區段。

- [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 描述支援 IntelliSense 參數資訊作業的必要功能，以在輸入方法時顯示方法簽章。

- [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 描述支援 IntelliSense 快速諮詢作業以顯示識別碼相關資訊所需的功能。

- [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 描述支援 IntelliSense 成員完成作業以從清單中選取命名空間成員所需的功能。

- [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 描述支援用來完成部分輸入單字的 IntelliSense 完成文字作業所需的功能。

- [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 描述當您進行調試時，語言服務可執行哪些動作來 **支援 [自動** 變數] 視窗。

- [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 描述如何使用編輯器視圖頂端的 **導覽** 列，以快速導覽至該視圖中所顯示之檔案中的任何類型或成員。

- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 說明支援原始程式碼的語法反白顯示所需的功能。

- [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 描述語言服務可執行哪些動作，以支援在偵錯工具之外驗證中斷點。

## <a name="related-sections"></a>相關章節
- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 描述執行使用 managed 封裝架構之語言服務的所有功能時，所需的剖析器和掃描器。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 說明使用 MPF 來執行語言服務時所需的功能。

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)

 說明使用註冊以 MPF 為基礎的語言服務時所需的步驟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [使用 IntelliSense](../../ide/using-intellisense.md)

 說明 IntelliSense 如何讓語言參考更容易存取。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 提供有關如何使用受管理的封裝架構 (MPF) 的資訊，以在受控碼中執行功能完整的語言服務。
