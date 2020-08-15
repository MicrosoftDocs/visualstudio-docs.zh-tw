---
title: 執行舊版語言 Service1 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2535c527fc3d2d94609246959c5293e455b9808d
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238734"
---
# <a name="implementing-a-legacy-language-service-1"></a>執行舊版語言服務1
您可以使用 managed package framework 中的類別 (MPF) 來執行舊版語言服務，以支援各種不同的功能，例如語法醒目提示、括弧對稱和 IntelliSense 完成。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語言服務的新方法，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)模組。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)

 在 MPF 中支援語言服務功能的總覽。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 說明使用 MPF 來執行語言服務時所需的功能。

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)

 說明使用註冊以 MPF 為基礎的語言服務時所需的步驟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 描述使用 MPF 來執行語言服務的所有功能時所需的兩個剖析器。

- [逐步解說：建立舊版語言服務](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 提供在 VSPackage 中執行 MPF 語言服務所需的基本步驟。

- [逐步解說：取得已安裝的程式碼片段 (舊版實作) 清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 示範用來抓取已安裝程式碼片段清單的技術。

- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)

 提供主題的連結，詳細說明必須執行哪些動作才能使用 MPF 來執行語言服務的所有功能。
