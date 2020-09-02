---
title: 擴充語言服務以支援 EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699577"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>支援您語言服務的 EditorConfig

[EditorConfig](https://editorconfig.org/) 檔案可讓您針對每個專案描述一般文字編輯器選項，例如縮排大小。 若要深入瞭解 Visual Studio 對 EditorConfig 檔案的支援，請參閱 [使用 EditorConfig 建立可移植的編輯器設定](../ide/create-portable-custom-editor-options.md)。

在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 但是，如果是索引標籤和空格等編輯，某些語言服務會選擇使用適當的內容文字視圖選項，而不是使用全域設定。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

以下是更新語言服務以支援 EditorConfig 檔案所需的變更，方法是使用_內容選項來_取代全域_語言特定_選項：

## <a name="indent-style"></a>縮排樣式

特定語言的選項 | 內容選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>縮排大小

特定語言的選項 | 內容選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>定位點大小

特定語言的選項 | 內容選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>另請參閱

- [使用 EditorConfig 建立可移植的編輯器設定](../ide/create-portable-custom-editor-options.md)
- [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)
