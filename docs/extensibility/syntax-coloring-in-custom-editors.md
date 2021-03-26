---
title: 自訂編輯器中的語法著色 |Microsoft Docs
description: 瞭解 Visual Studio 環境 SDK 自訂編輯器中的語法著色，以顯示指定檔視圖的指定色彩。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06cd4ae1db1187cc650a4fd9486f4b1686c6b015
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063691"
---
# <a name="syntax-coloring-in-custom-editors"></a>自訂編輯器中的語法著色
Visual Studio 環境 SDK 編輯器，包括核心編輯器，請使用語言服務來識別特定的語法專案，並以指定的檔查看色彩來顯示這些專案。

## <a name="colorization-requirements"></a>顏色標示需求
 所有執行語言服務著色器的編輯器都必須：

1. 使用物件來執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 管理要以色彩標示的文字，以及執行的物件， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 以提供文字的檔查看。

2. 使用語言服務的識別 GUID 來查詢 VSPackage 的服務提供者，以取得特定語言服務的介面。

3. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 物件的方法來執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 。 這個方法會將語言服務與 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage 用來管理要以色彩標示之文字的實作為關聯。

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>語言服務的著色器使用核心編輯器
 當核心編輯器的實例取得具有著色器的語言服務時，語言服務的著色器會自動進行文字的剖析和轉譯，而不需要對您的部分採取任何進一步的介入。

 IDE 會以透明的方式：

- 視需要呼叫著色器，以便在執行中加入或修改文字時進行剖析和分析 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 。

- 確定 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 使用著色器傳回的資訊更新和重新繪製由執行所提供的檔視圖所提供的顯示。

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>語言服務著色器的非核心編輯器使用方式
 非核心編輯器實例也可以使用語言服務的語法顏色標示服務，但必須明確地取出和套用服務的著色器，並重新繪製其檔視圖本身。

 若要這樣做，非核心的編輯器必須：

1. 取得語言服務的著色器物件 (其會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 並 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>) 。 VSPackage 藉由呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 語言服務介面上的方法來執行此操作。

2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法來要求以色彩標示特定範圍的文字。

     方法會傳回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 值的陣列，以色彩標示文字範圍中的每個字母都會有一個陣列。 它也會將文字範圍識別為特定類型的可設定色彩專案，例如批註、關鍵字或資料類型。

3. 使用所傳回的顏色標示資訊 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> ，以重新繪製和顯示其文字。

> [!NOTE]
> 除了使用語言服務的著色器之外，VSPackage 也可以選擇使用一般用途 Visual Studio 環境 SDK 文字著色機制。 如需此機制的詳細資訊，請參閱 [使用字型和色彩](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015)。

## <a name="see-also"></a>另請參閱

- [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [實作語法著色](../extensibility/internals/implementing-syntax-coloring.md)
- [如何︰使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../extensibility/internals/custom-colorable-items.md)