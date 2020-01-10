---
title: 擴充編輯器和語言服務 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af1fa0222be9630a495a43204d7a973341190131
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186663"
---
# <a name="extend-the-editor-and-language-services"></a>擴充編輯器和語言服務
您可以將語言服務功能（例如 IntelliSense）新增至您自己的編輯器，並擴充 Visual Studio 程式碼編輯器的大部分功能。  如需您可以擴充之內容的完整清單，請參閱[語言服務和編輯器延伸模組點](../extensibility/language-service-and-editor-extension-points.md)。

 您可以使用 Managed Extensibility Framework （MEF）來擴充大部分的編輯器功能。 例如，如果您想要擴充的編輯器功能是語法著色，您可以撰寫 MEF*元件部分*，以定義您想要不同色彩的分類，以及您要如何處理它們。 編輯器也支援相同功能的多個延伸模組。

 編輯器展示層是以 Windows Presentation Framework （WPF）為基礎。 WPF 提供圖形程式庫來進行彈性的文字格式設定，同時也提供圖形和動畫等視覺效果。

 Visual Studio SDK 會提供稱為「*填充*碼」的介面卡，以支援針對較早版本所撰寫的 vspackage。 不過，如果您有現有的 VSPackage，建議您將其更新為新的技術，以取得更佳的效能和可靠性。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[開始使用語言服務和編輯器延伸模組](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|說明如何建立編輯器的延伸模組。|
|[在編輯器中](../extensibility/inside-the-editor.md)|描述編輯器的一般結構，並列出其部分功能。|
|[在編輯器中 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|說明如何搭配使用 Managed Extensibility Framework （MEF）與編輯器。|
|[語言服務和編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)|列出編輯器的擴充點。 擴充點代表可以擴充的編輯器功能。|
|[逐步解說：建立視圖裝飾、命令和設定（資料行輔助線）](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|逐步解說並說明如何建立可繪製資料行輔助線的視圖裝飾，以協助您將程式碼保持在特定的顯示寬度。  也會顯示讀取和寫入設定，以及宣告和執行可從命令視窗叫用的命令。|
|[編輯器匯入](../extensibility/editor-imports.md)|列出擴充功能可以匯入的服務。|
|[將舊版程式碼調整為編輯器](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|說明調整舊版程式碼（預先 Visual Studio 2010）以擴充編輯器的不同方式。|
|[遷移舊版語言服務](../extensibility/internals/migrating-a-legacy-language-service.md)|說明如何遷移以 VSPackage 為基礎的語言服務。|
|[逐步解說：將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|顯示如何將內容類型連結至副檔名。|
|[逐步解說：建立邊界字元](../extensibility/walkthrough-creating-a-margin-glyph.md)|顯示如何將圖示新增至邊界。|
|[逐步解說：反白顯示文字](../extensibility/walkthrough-highlighting-text.md)|示範如何使用*標記*來反白顯示文字。|
|[逐步解說：加入大綱](../extensibility/walkthrough-outlining.md)|示範如何新增特定大括弧類型的大綱。|
|[逐步解說：顯示成對的大括弧](../extensibility/walkthrough-displaying-matching-braces.md)|顯示如何反白顯示成對的括弧。|
|[逐步解說：顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|示範如何顯示描述程式碼專案（例如屬性、方法和事件）的 QuickInfo 快顯視窗。|
|[逐步解說：顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)|示範如何顯示快顯視窗，以提供簽章中參數數目和類型的相關資訊。|
|[逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)|顯示如何執行語句完成。|
|[逐步解說：執行程式碼片段](../extensibility/walkthrough-implementing-code-snippets.md)|示範如何執行程式碼片段擴充。|
|[逐步解說：顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|顯示如何顯示程式碼建議的淺燈泡。|
|[逐步解說：搭配編輯器延伸模組使用 shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|示範如何將 VSPackage 中的功能表命令與 MEF 元件產生關聯。|
|[逐步解說：搭配使用快速鍵與編輯器延伸模組](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|顯示如何將 VSPackage 中的功能表快捷方式與 MEF 元件產生關聯。|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|提供 Managed Extensibility Framework （MEF）的相關資訊。|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|提供 Windows Presentation Foundation （WPF）的相關資訊。|

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