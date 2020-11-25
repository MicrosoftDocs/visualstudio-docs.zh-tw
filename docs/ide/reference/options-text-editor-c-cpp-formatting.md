---
title: 選項、文字編輯器、C/C++、格式設定
description: 瞭解如何在使用 C 和 c + + 進行程式設計時，使用 [格式化選項] 頁面及其子頁面來設定程式碼編輯器中格式化程式碼的選項。
ms.custom: SEO-VS-2020
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 264485fd8f20ee31046035dba7b208795d0d91b0
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041083"
---
# <a name="options-text-editor-cc-formatting"></a>選項、文字編輯器、C/C++、格式設定

在使用 C 或 C++ 進行程式設計時，請使用這些屬性頁變更程式碼編輯器的預設行為。

![C++ Formatting 屬性頁](media/cpp-formatting.png)

若要存取這個頁面，請在 [選項] 對話方塊的左窗格中依序展開 [文字編輯器] 和 [C/C++]，然後按一下 [格式]。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="general-page"></a>一般頁面

此頁面包含在您鍵入時格式化陳述式和區塊的選項。

::: moniker range="vs-2017"

**Visual Studio 2017 15.7 版和更新版本**：

::: moniker-end

頁面也有設定 [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) 5.0 版支援的選項。 ClangFormat 是一個公用程式，可讓您更輕鬆地根據一組可以在 .clang-format 或 _clang-format 檔案中設定的規則，設定程式碼的樣式和格式化。

### <a name="configuring-clangformat-options"></a>設定 ClangFormat 選項

::: moniker range="vs-2017"

**Visual Studio 2017 15.7 版和更新版本**：

::: moniker-end

預設會啟用 ClangFormat 支援。 您可以選擇要將這些常見格式設定慣例的哪一項，套用至所有專案：LLVM、Google、Chrome、Mozilla 或 WebKit。 您也可以建立自訂的格式定義 .clang-format 或 _clang-format 檔案。 如果這樣的檔案存在於專案資料夾，則 Visual Studio 會使用它來格式化該資料夾及其子資料夾中的所有原始程式碼檔。

根據預設，Visual Studio 在背景中執行 clangformat.exe，並在您鍵入時套用格式。 您也可以指定只針對以手動方式叫用的格式化命令 **格式化文件 (Ctrl+K、Ctrl+D)** 或 **格式化選取範圍 (Ctrl+K、Ctrl+F)** 來執行它。

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>縮排、新行、間距文繞圖頁面

這些頁面能啟用各種格式化自訂，但如果已啟用 ClangFormat 便會被忽略。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
- [使用 IntelliSense](../../ide/using-intellisense.md)
