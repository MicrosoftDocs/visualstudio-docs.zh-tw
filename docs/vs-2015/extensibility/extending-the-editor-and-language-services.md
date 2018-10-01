---
title: 擴充編輯器和語言服務 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8102b8fb4afc02ca0540d75b3c0d08ef75b964d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496743"
---
# <a name="extending-the-editor-and-language-services"></a>延伸編輯器和語言服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[擴充編輯器和語言服務](https://docs.microsoft.com/visualstudio/extensibility/extending-the-editor-and-language-services)。  
  
您可以將語言服務功能 （例如 IntelliSense) 新增至您自己的編輯器，並擴充 Visual Studio 程式碼編輯器的大部分功能。  您可以擴充的完整清單，請參閱 <<c0> [ 語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)。  
  
 您可以使用 Managed Extensibility Framework (MEF)，以擴充編輯器的大部分功能。 例如，如果您想要擴充的編輯器功能的語法著色，您可以撰寫 MEF*元件部分*，定義要為其不同的色彩，以及您所想要處理的分類。 此編輯器也支援多個擴充功能的相同功能。  
  
 編輯器展示層為基礎的 Windows Presentation Framework (WPF)。 WPF 圖形程式庫提供彈性的文字格式設定，並提供視覺效果，例如圖形和動畫。  
  
 Visual Studio SDK 提供稱為介面卡*填充碼*支援是針對較早版本所撰寫的 Vspackage。 不過，如果您有現有的 VSPackage，建議其更新為新的技術，來取得較佳的效能和可靠性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[開始使用語言服務及編輯器擴充功能](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|說明如何建立編輯器延伸模組。|  
|[深入探索編輯器](../extensibility/inside-the-editor.md)|描述編輯器的一般結構，並列出其部分功能。|  
|[編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|說明如何使用 Managed Extensibility Framework (MEF) 使用編輯器。|  
|[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)|列出編輯器 的擴充點。 擴充點代表可擴充的編輯器功能。|  
|[逐步解說︰建立檢視裝飾、命令和設定 (分欄輔助線)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|逐步解說，並說明建置繪製資料行 gudie 幾行，以協助您保持為特定的顯示寬度的程式碼檢視裝飾。  也會顯示讀取和寫入設定，以及宣告和實作，您可以從 [命令] 視窗叫用的命令。|  
|[編輯器匯入](../extensibility/editor-imports.md)|列出擴充功能可以匯入的服務。|  
|[使舊版程式碼配合編輯器](../extensibility/adapting-legacy-code-to-the-editor.md)|說明不同的方式，來調整 (預先 Visual Studio 2010) 來擴充編輯器的舊版程式碼。|  
|[移轉舊版語言服務](../extensibility/internals/migrating-a-legacy-language-service.md)|說明如何將基礎的 VSPackage 語言服務。|  
|[逐步解說︰將內容類型連結至副檔名](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|示範如何將內容類型連結至檔案的副檔名。|  
|[逐步解說：建立邊界字符](../extensibility/walkthrough-creating-a-margin-glyph.md)|示範如何將圖示新增至邊界。|  
|[逐步解說︰反白顯示文字](../extensibility/walkthrough-highlighting-text.md)|示範如何使用*標記*反白顯示文字。|  
|[逐步解說︰大綱](../extensibility/walkthrough-outlining.md)|示範如何新增特定種類的大括號的大綱。|  
|[逐步解說︰顯示對稱的括號](../extensibility/walkthrough-displaying-matching-braces.md)|示範如何反白顯示對稱的括號。|  
|[逐步解說︰顯示 QuickInfo 工具提示](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|示範如何顯示 QuickInfo 快顯視窗描述項目，例如屬性、 方法和事件的程式碼。|  
|[逐步解說︰顯示簽章說明](../extensibility/walkthrough-displaying-signature-help.md)|示範如何顯示簽章中提供的參數類型與數量的相關資訊的快顯功能表。|  
|[逐步解說：顯示陳述式完成](../extensibility/walkthrough-displaying-statement-completion.md)|示範如何實作陳述式完成。|  
|[逐步解說︰實作程式碼片段](../extensibility/walkthrough-implementing-code-snippets.md)|示範如何實作程式碼片段擴充。|  
|[逐步解說︰顯示燈泡建議](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|示範如何顯示燈泡，如程式碼的建議。|  
|[逐步解說︰搭配編輯器擴充功能使用 Shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|示範如何在 VSPackage 中的功能表命令相關聯的 MEF 元件。|  
|[逐步解說︰搭配編輯器擴充功能使用快速鍵](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|示範如何在 VSPackage 中的功能表捷徑關聯為 MEF 元件。|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|提供 Managed Extensibility Framework (MEF) 的相關資訊。|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|提供 Windows Presentation Foundation (WPF) 的相關資訊。|  
  
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

