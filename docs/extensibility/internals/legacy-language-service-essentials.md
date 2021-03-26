---
title: 舊版語言服務基本知識 |Microsoft Docs
description: 瞭解可讓您將程式設計語言整合至 Visual Studio 的舊版語言服務所提供的基本功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa3fc358e7557360f02a80f108bcbec74ae48e5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074557"
---
# <a name="legacy-language-service-essentials"></a>舊版語言服務的基本資訊
您必須提供語言服務，才能將程式設計語言整合至 Visual Studio。 本主題說明舊版語言服務中提供的功能。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語言服務的新方法，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

 舊版語言服務提供下列功能：

|功能|描述|
|-------------|-----------------|
|語法標色|讓編輯器視圖顯示不同語言元素的不同色彩和字型樣式。 這種差異可讓您更輕鬆地讀取和編輯檔案。<br /><br /> 如需一般資訊，請參閱 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。<br /><br /> 如需受管理套件架構 (MPF) 中這項功能的相關資訊，請參閱 [舊版語言服務中的語法標示](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。|
|陳述式完成|完成使用者已開始鍵入的語句或關鍵字。 語句完成可協助使用者更輕鬆地進入困難的語句，並減少輸入的機率，並減少錯誤的機率。<br /><br /> 如需一般資訊，請參閱 [舊版語言服務中的語句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。<br /><br /> 如需有關 MPF 中這項功能的詳細資訊，請參閱 [舊版語言服務中的 Word 自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)。|
|括號對稱|反白顯示成對的字元，例如大括弧。 當使用者輸入結尾字元（例如 "}"）時，大括弧比對會反白顯示對應的開頭字元，例如 "{"。 當有數個層級的封入字元時，此功能可協助使用者確認封入字元已正確配對。<br /><br /> 如需有關 MPF 中這項功能的詳細資訊，請參閱 [舊版語言服務中的括弧](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)比對。|
|參數資訊工具提示|顯示使用者目前輸入之多載方法的可能簽章清單。<br /><br /> 如需一般資訊，請參閱 [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。<br /><br /> 如需有關 MPF 中這項功能的詳細資訊，請參閱 [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)。|
|錯誤標記|在語法不正確的文字下，顯示波浪式紅色底線（也稱為曲線）。 錯誤標記通常用來讓使用者知道拼錯的關鍵字、未封閉的括弧、不正確字元，以及類似的錯誤。<br /><br /> 在 MPF 類別中，會在類別的方法中自動處理錯誤標記 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> 。|

 其中許多功能都需要語言服務來剖析原始程式碼。 您通常可以重複使用編譯器或解譯器的 token 化和剖析程式碼。

 下列功能與程式設計語言的支援相關，但不是語言服務的一部分：

| 功能 | 描述 |
|-----------------------| - |
| 運算式評估工具 | 藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由驗證中斷點和提供要在 [自動變數] 的 [自動偵測] 視窗中顯示的運算式清單，支援偵錯工具。<br /><br /> For more information, see [Language Service Support for Debugging](../../extensibility/internals/language-service-support-for-debugging.md). |
| 符號流覽工具 | 支援 **物件瀏覽器**、 **類別檢視**、 **呼叫瀏覽器** 和 **尋找符號結果**。 |
