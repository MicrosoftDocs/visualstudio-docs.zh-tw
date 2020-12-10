---
title: 擴充編輯器和語言服務 |Microsoft Docs
description: 您可以將語言服務功能加入編輯器，並擴充 Visual Studio 程式碼編輯器的功能。 瞭解 Managed Extensibility Framework。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d4b76fe7feadb4458ef68acb351b81c6fa494c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995742"
---
# <a name="extend-the-editor-and-language-services"></a>擴充編輯器和語言服務
您可以將語言服務功能 (例如 IntelliSense) 加入您自己的編輯器，並擴充 Visual Studio 程式碼編輯器的大部分功能。  如需可延伸之內容的完整清單，請參閱 [語言服務和編輯器延伸點](../extensibility/language-service-and-editor-extension-points.md)。

 您可以使用 Managed Extensibility Framework (MEF) 來擴充大部分的編輯器功能。 例如，如果您想要擴充的編輯器功能是語法色彩，您可以撰寫 MEF *元件元件* 來定義您想要使用不同色彩的分類，以及要如何處理這些分類。 編輯器也支援相同功能的多個擴充功能。

 編輯器展示層是以 Windows Presentation Framework (WPF) 為基礎。 WPF 提供圖形程式庫以提供彈性的文字格式，也提供圖形和動畫等視覺效果。

 Visual Studio SDK 提供稱為 *填充* 碼的介面卡，以支援針對較早版本所撰寫的 vspackage。 儘管如此，如果您有現有的 VSPackage，我們建議您將其更新為新的技術，以取得更佳的效能和可靠性。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[開始使用語言服務及編輯器擴充功能](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|說明如何建立編輯器的延伸模組。|
|[在編輯器內](../extensibility/inside-the-editor.md)|描述編輯器的一般結構，並列出其部分功能。|
|[編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|說明如何搭配使用 Managed Extensibility Framework (MEF) 與編輯器。|
|[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)|列出編輯器的延伸點。 擴充點代表可延伸的編輯器功能。|
|[逐步解說：建立視圖裝飾、命令和設定 (資料行指南) ](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|逐步解說並說明如何建立可繪製資料行輔助線的視圖裝飾，以協助您將程式碼保持在特定的顯示寬度。  也會顯示讀取和寫入設定，以及宣告和執行可從命令視窗叫用的命令。|
|[編輯器匯入](../extensibility/editor-imports.md)|列出延伸模組可以匯入的服務。|
|[將舊版程式碼調整為編輯器](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|說明調整舊版程式碼 (預先 Visual Studio 2010) 擴充編輯器的不同方式。|
|[遷移舊版語言服務](../extensibility/internals/migrating-a-legacy-language-service.md)|說明如何遷移以 VSPackage 為基礎的語言服務。|
|[逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|顯示如何將內容類型連結至副檔名。|
|[逐步解說：建立邊界字元](../extensibility/walkthrough-creating-a-margin-glyph.md)|顯示如何將圖示新增至邊界。|
|[逐步解說：反白顯示文字](../extensibility/walkthrough-highlighting-text.md)|顯示如何使用 *標記* 來反白顯示文字。|
|[逐步解說：加入大綱](../extensibility/walkthrough-outlining.md)|示範如何針對特定類型的大括弧加入大綱。|
|[逐步解說：顯示成對的大括弧](../extensibility/walkthrough-displaying-matching-braces.md)|顯示如何反白顯示成對的大括弧。|
|[逐步解說：顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|示範如何顯示 QuickInfo 快顯視窗，以描述程式碼的元素，例如屬性、方法和事件。|
|[逐步解說：顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)|示範如何顯示快顯視窗，以提供簽章中參數數目和類型的相關資訊。|
|[逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)|顯示如何執行語句完成。|
|[逐步解說：執行程式碼片段](../extensibility/walkthrough-implementing-code-snippets.md)|顯示如何執行程式碼片段展開。|
|[逐步解說：顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|示範如何顯示程式碼建議的 light 燈泡。|
|[逐步解說：搭配編輯器延伸模組使用 shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|顯示如何將 VSPackage 中的功能表命令與 MEF 元件產生關聯。|
|[逐步解說：搭配編輯器延伸模組使用快速鍵](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|顯示如何將 VSPackage 中的功能表快捷方式與 MEF 元件產生關聯。|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|提供 Managed Extensibility Framework (MEF) 的相關資訊。|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|提供 Windows Presentation Foundation (WPF) 的相關資訊。|

## <a name="reference"></a>參考資料
 Visual Studio 編輯器包含下列命名空間。

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>