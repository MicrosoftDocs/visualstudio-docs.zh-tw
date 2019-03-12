---
title: 選項、文字編輯器、C/C++、實驗
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ee70d3cf580caaea4207f1d830ef1500f18942ff
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57221391"
---
# <a name="options-text-editor-cc-experimental"></a>選項、文字編輯器、C/C++、實驗

藉由變更這些選項，您可以變更進行 C 或 C++ 程式設計時之 IntelliSense 和瀏覽資料庫的相關行為。 這些功能是實驗性功能，可能會修改或從 Visual Studio 未來版本中移除。

::: moniker range="vs-2017"

本文描述 Visual Studio 2017 中的選項。 針對 Visual Studio 2015，請在目錄上方的選取器中選取 [2015]。

::: moniker-end

若要存取本屬性頁面，請按 **Control** + **Q** 啟動 `Quick Launch`，然後鍵入 "experimental"。 鍵入前幾個字母之後，快速啟動就會找到頁面。 您也可以選擇 [工具] > [選項]，並依序展開 [文字編輯器] 和 [C/C++]，然後選擇 [實驗性]，即可到達頁面。

這些功能可在 Visual Studio 安裝中使用。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="enable-predictive-intellisense"></a>啟用預測性 IntelliSense

預測性 IntelliSense 會限制顯示在 IntelliSense 下拉式清單中的結果數，讓您只看到內容相關的結果。 例如，如果您鍵入 <code>int x =</code> 並叫用 IntelliSense 下拉式清單，則只會看到整數或傳回整數的函式。 根據預設，會關閉預測性 IntelliSense。

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>啟用更快的專案載入

在 Visual Studio 2017 15.3 版中，這項功能稱為**啟用專案快取**，並已移至 [VC++ 專案設定](vcpp-project-settings-projects-and-solutions-options-dialog-box.md)屬性頁。

這個選項讓 Visual Studio 能夠快取專案資料，以便在您下次開啟專案時，載入那份快取的資料，而不必重新從專案檔計算資料。 使用快取資料可以大幅加速專案載入時間。

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Visual Studio Marketplace 中的其他功能

您可以瀏覽 [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads) 中的其他文字編輯器功能。 [C++ 快速修正](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)即為一例，其支援下列項目：

- **加入遺漏的 #include** - 建議相關的 #include 來表示程式碼中的未知符號

- **加入 Using 命名空間/完整限定符號** - 類似上一個項目，但針對命名空間

- **加入遺漏的分號**

- **線上說明** - 在線上說明中搜尋錯誤訊息

- 等等...

## <a name="see-also"></a>另請參閱

- [設定語言特定編輯器選項](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
) (在 C++ 中重構 (VC 部落格))
