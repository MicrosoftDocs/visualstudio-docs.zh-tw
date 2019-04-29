---
title: 擴充 Visual Studio 中支援 EditorConfig 語言服務 |Microsoft Docs
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c29c22ae4539d874ffc08c9ce5adf94ab33d404
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799859"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>支援 EditorConfig 語言服務

[EditorConfig](http://editorconfig.org/)檔案可讓您根據每個專案描述一般文字編輯器選項，例如縮排大小。 若要深入了解 Visual Studio 支援 EditorConfig 檔案，請參閱[建立可移植的編輯器設定使用 EditorConfig](../ide/create-portable-custom-editor-options.md)。

在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 不過，進行編輯，例如定位點和空格，有些語言服務選擇使用適當的內容文字檢視 選項，而不是使用全域設定。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

以下是變更所需的更新語言服務以支援 EditorConfig 檔案，來取代全域_語言特有_選項搭配_內容_選項：

## <a name="indent-style"></a>縮排樣式

語言特有的選項 | 內容相關的選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>縮排大小

語言特有的選項 | 內容相關的選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>定位點大小

語言特有的選項 | 內容相關的選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>另請參閱

- [建立使用 EditorConfig 的可攜式的編輯器設定](../ide/create-portable-custom-editor-options.md)
- [擴充的編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)