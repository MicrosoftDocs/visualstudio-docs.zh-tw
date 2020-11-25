---
title: 選項、文字編輯器、C/C++、檢視
description: 瞭解如何使用 C/c + + 區段中的 [視圖] 頁面，在 Visual Studio 中變更程式碼波浪線、非使用中程式碼、大綱等的預設行為。
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 68d08953ca3c493f3b3e42dd4ddd84bc19bdfd6e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041070"
---
# <a name="options-text-editor-cc-view"></a>選項、文字編輯器、C/C++、檢視

在使用 C 或 C++ 進行程式設計時，請使用這些屬性頁變更程式碼編輯器的預設行為。

若要存取這個屬性頁，請依序選擇 [**工具**  >  **選項**] 和 [**文字編輯器**]、[ **c/c + +**]，然後選擇 [ **View**]。

## <a name="code-squiggles"></a>程式碼波浪線

您可以啟用或停用下列設定來管理文字編輯器處理 C 和 C++ 程式碼波浪線的方式：

- **略過瀏覽區域中的巨集** - 定義如何透過瀏覽資料庫醒目提示略過區域內的巨集，例如定義包含大括弧的巨集。

- **可轉換為 constexpr 的巨集** - 定義如何醒目提示可以轉換為 `constexpr` 定義的巨集定義。

## <a name="inactive-code"></a>非現用程式碼

- **顯示非使用中區塊** - 前置處理器的非使用中區塊會以不同色彩標示。

- **停用非使用中程式碼不透明度** - 單色會用於代替非使用中程式碼區塊的不透明度。

- **非使用中程式碼不透明度百分比** - 非使用中程式碼區塊的不透明度百分比。

## <a name="miscellaneous"></a>其他

- **列舉註解工作** - 掃描開啟中的原始程式檔以找出 VS 語彙基元，然後將其回報於 [工作清單] 視窗中。

- **醒目提示相符的語彙基元** - 醒目提示與游標位置相符的右括弧或語法。

## <a name="outlining"></a>大綱

- **啟用大綱** - 當檔案開啟時進入大綱模式。

- **大綱 Pragma 區域** - 自動大綱 `#pragma` 區域區塊。

- **大綱陳述式區塊** - 自動大綱陳述式區塊。

## <a name="see-also"></a>另請參閱

- [設定 Language-Specific 編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/) (在 C++ 中重構 (VC 部落格))
