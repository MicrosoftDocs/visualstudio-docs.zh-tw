---
title: 擴充語言服務以支援 EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 663a87ba15121896edcb4c049e7adc6b5c38492a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983109"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>支援語言服務的 EditorConfig

[EditorConfig](https://editorconfig.org/)檔案可讓您以每個專案為基礎，描述一般文字編輯器選項，例如縮排大小。 若要深入瞭解 Visual Studio 對 EditorConfig 檔案的支援，請參閱[使用 EditorConfig 建立可攜的編輯器設定](../ide/create-portable-custom-editor-options.md)。

在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 不過，對於索引標籤和空格之類的編輯，有些語言服務選擇使用適當的內容文字查看選項，而不是使用全域設定。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

以下是更新語言服務以支援 EditorConfig 檔案所需的變更，方法是以_內容選項取代_全域_語言特定的_選項：

## <a name="indent-style"></a>縮排樣式

語言特定選項 | 內容相關選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>縮排大小

語言特定選項 | 內容相關選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>定位點大小

語言特定選項 | 內容相關選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>請參閱

- [使用 EditorConfig 建立可攜的編輯器設定](../ide/create-portable-custom-editor-options.md)
- [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)