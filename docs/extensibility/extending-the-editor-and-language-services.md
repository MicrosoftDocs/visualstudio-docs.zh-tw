---
title: 延伸編輯器和語言服務 |微軟文件
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
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711705"
---
# <a name="extend-the-editor-and-language-services"></a>延伸編輯器和語言服務
您可以將語言服務功能(如 IntelliSense)添加到您自己的編輯器中,並擴展 Visual Studio 代碼編輯器的大多數功能。  有關可以擴充的內容的完整清單,請參考[語言服務與編輯器延伸點](../extensibility/language-service-and-editor-extension-points.md)。

 您可以使用託管擴充性框架 (MEF) 擴展大多數編輯器功能。 例如,如果要擴展的編輯器功能是語法著色,則可以編寫一個 MEF*元件部件*,用於定義需要不同顏色的分類以及您希望它們的處理方式。 編輯器還支援同一功能的多個擴展。

 編輯器表示層基於 Windows 演示文稿框架 (WPF)。 WPF 提供了用於靈活文本格式的圖形庫,還提供圖形和動畫等可視化效果。

 Visual Studio SDK 提供稱為*hims*的適配器,以支援為早期版本編寫的 VS 包。 但是,如果您有現有的 VSPackage,我們建議您將其更新到新技術,以獲得更好的性能和可靠性。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[開始使用語言服務及編輯器延伸](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|說明如何創建編輯器的擴展。|
|[編輯器內部](../extensibility/inside-the-editor.md)|描述編輯器的一般結構,並列出它的一些功能。|
|[編輯器中的托管擴充性框架](../extensibility/managed-extensibility-framework-in-the-editor.md)|說明如何使用託管擴展框架 (MEF) 與編輯器。|
|[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)|列出編輯器的擴展點。 擴展點表示可擴展的編輯器功能。|
|[演練:建立檢視裝飾、指令和設定(列參考線)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|遍通並解釋構建一個檢視修飾,繪製列引導線,以説明您將代碼保持在特定的顯示寬度。  還顯示讀取和寫入設置以及聲明和實現可以從命令視窗調用的命令。|
|[編輯器匯入](../extensibility/editor-imports.md)|列出擴展可以導入的服務。|
|[將舊代碼調整到編輯器](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|解釋調整舊版代碼(Visual Studio 2010 前)以擴展編輯器的不同方法。|
|[遷移舊語言服務](../extensibility/internals/migrating-a-legacy-language-service.md)|說明如何遷移基於 VSPackage 的語言服務。|
|[演練:將內容類型連結到檔案名副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|展示如何將內容類型連結到檔名副檔名。|
|[演練:建立邊距字形](../extensibility/walkthrough-creating-a-margin-glyph.md)|演示如何向邊距添加圖示。|
|[演練:突顯文字](../extensibility/walkthrough-highlighting-text.md)|展示如何使用*標記*突顯文字。|
|[演練:添加大綱](../extensibility/walkthrough-outlining.md)|演示如何添加特定類型的大括弧的大綱。|
|[演練:顯示匹配的大括弧](../extensibility/walkthrough-displaying-matching-braces.md)|演示如何突出顯示匹配的大括弧。|
|[演練:顯示快速資訊工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|展示如何顯示描述代碼元素(如屬性、方法和事件)的 QuickInfo 彈出視窗。|
|[演練:顯示簽名說明](../extensibility/walkthrough-displaying-signature-help.md)|展示如何顯示提供簽名中參數數和類型信息的彈出視窗。|
|[逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)|演示如何實現語句完成。|
|[演練:實現代碼段](../extensibility/walkthrough-implementing-code-snippets.md)|演示如何實現代碼段擴展。|
|[演練:顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|演示如何顯示燈泡以進行代碼建議。|
|[演練:使用具有編輯器延伸的 shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|演示如何將 VSPackage 中的功能表命令與 MEF 元件相關聯。|
|[演練:使用帶有編輯器延伸的捷徑](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|展示如何將 VSPackage 中的選單快捷方式與 MEF 元件相關聯。|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|提供有關託管擴充性框架 (MEF) 的資訊。|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|提供有關 Windows 演示文稿基礎 (WPF) 的資訊。|

## <a name="reference"></a>參考
 Visual Studio 編輯器包括以下命名空間。

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
