---
title: "擴充 Visual Studio 中支援 EditorConfig 語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9b38601953fd5b1c80e5eeffd75c2fdc2608fc73
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-editorconfig-for-your-language-service"></a>支援 EditorConfig 語言服務

[EditorConfig](http://editorconfig.org/)檔則可讓您根據每個專案描述常見的文字編輯器選項，例如縮排大小。 若要深入了解 Visual Studio 支援 EditorConfig 檔案，請參閱[建立可攜式編輯器設定使用 EditorConfig](../ide/create-portable-custom-editor-options.md)。

在大部分情況下，當您實作 Visual Studio 語言服務時，並不需要進行任何額外的作業即可支援 EditorConfig 通用屬性。 當使用者開啟檔案時，核心編輯器會自動探索並讀取 .editorconfig 檔案，然後設定適當的文字緩衝區和檢視選項。 不過，例如定位點和空格的編輯，有些語言服務選擇使用適當內容的文字檢視 選項，而不是使用全域設定。 在這種情況下，您必須更新語言服務才能支援 EditorConfig 檔案。

以下是更新以支援 EditorConfig 檔案來取代全域語言服務所需的變更_語言特有_選項與_內容_選項：

## <a name="indent-style"></a>縮排樣式

語言特有的選項 | 內容的選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>縮排大小

語言特有的選項 | 內容的選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>定位點大小

語言特有的選項 | 內容的選項
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>另請參閱

[建立使用 EditorConfig 可攜式編輯器設定](../ide/create-portable-custom-editor-options.md)  
[擴充的編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)