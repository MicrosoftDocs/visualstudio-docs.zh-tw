---
title: 延伸語言服務以支援編輯器設定
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699577"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>為您的語言服務提供編輯器設定

[EditorConfig](https://editorconfig.org/)檔案使您能夠按專案描述常見的文本編輯器選項,如縮進大小。 要瞭解有關 Visual Studio 支援編輯器設定檔的詳細資訊,請參考使用[Editor Config 建立可攜式編輯器設定](../ide/create-portable-custom-editor-options.md)。

在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 但是,對於選項卡和空格等編輯,某些語言服務選擇使用適當的上下文文本視圖選項,而不是使用全域設置。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

以下是更新語言服務以支援 Editor Config 檔案所需的變更,這些變更將特定於全域_的語言_選項取代為_上下文_選項:

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

- [使用編輯器設定建立可攜式編輯器設定](../ide/create-portable-custom-editor-options.md)
- [延伸編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)
