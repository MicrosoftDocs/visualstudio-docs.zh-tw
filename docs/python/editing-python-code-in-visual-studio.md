---
title: "在 Visual Studio 中編輯 Python 程式碼 | Microsoft Docs"
description: "在 Visual Studio 中編輯 Python 可提供 IntelliSense、程式碼片段及巡覽功能，還有格式設定、Linting 和重構。"
ms.custom: 
ms.date: 02/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 375508647c7a192b7b3869c4faaf80b8df2d0a4a
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="editing-python-code"></a>編輯 Python 程式碼

開發人員大部分的時間都花在程式碼編輯器中，所以 [Visual Studio 中的 Python 支援](installing-python-support-in-visual-studio.md)提供的功能可協助您提高生產力。 功能包括了 IntelliSense 語法反白顯示、自動完成、簽章說明、方法覆寫、搜尋和瀏覽。

編輯器也與 Visual Studio 中的互動式視窗整合，在兩者間交換程式碼變得更輕鬆。 如需詳細資訊，請參閱[教學課程步驟 3：使用互動式 REPL 視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)和[使用互動式視窗 - 將程式碼傳送至互動式命令](python-interactive-repl-in-visual-studio.md#send-code-to-interactive-command)。

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看示範編輯 Python 程式碼的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) \(英文\) (2 分 30 秒)。|

如需在 Visual Studio 中編輯程式碼的一般文件，請參閱[在程式碼和文字編輯器中撰寫程式碼](../ide/writing-code-in-the-code-and-text-editor.md)。 另請參閱 [Visual Studio 中的大綱](../ide/outlining.md)，這有助您專注於特定的程式碼區段。

您也可以使用 Visual Studio 物件瀏覽器 ([檢視] > [其他視窗] > [物件瀏覽器] 或 Ctrl+W、J) 來檢查每個模組中定義的 Python 類別，以及這些類別中定義的函式。

## <a name="intellisense"></a>IntelliSense

IntelliSense 提供[自動完成](#completions)、[簽章說明](#signature-help)、[快速諮詢](#quick-info)和[程式碼著色](#code-coloring)。 為了改善效能，IntelliSense 仰賴為您專案中的每個 Python 環境所產生的自動完成資料庫。 如果新增、移除或更新套件，資料庫可能需要重新整理。 資料庫狀態會顯示在 [IntelliSense] 索引標籤的 [Python 環境] 視窗中 (方案總管的同層級) (請參閱 [Python 環境](managing-python-environments-in-visual-studio.md))。 

### <a name="completions"></a>自動完成

自動完成會顯示為陳述式、識別碼和其他適合在編輯器目前的位置中輸入的文字。 清單中顯示的資訊會以內容為依據，並會經過篩選以省略不正確或令人分心的選項。 輸入不同的陳述式 (例如 `import`) 和運算子 (包括句點) 通常會觸發自動完成，但您隨時可以輸入 Ctrl-J 和空格讓它們顯示。

![成員自動完成](media/code-editing-completions-simple.png)

自動完成清單開啟後，您可以使用方向鍵、滑鼠來搜尋您想要的自動完成內容，或是繼續輸入。 隨著您輸入更多字元，清單會進一步篩選以顯示可能的自動完成內容。 您也可以使用快速鍵，例如：

- 輸入不在名稱開頭的字母，例如，輸入 'parse' 以尋找 'argparse'
- 只輸入每個字組開頭的字母，例如，輸入 'abc' 以尋找 'AbstractBaseClass'，或輸入 'air' 以尋找 'as_integer_ratio'
- 略過字母 (例如 'b64') 以尋找 'base64'

一些範例如下：

![具篩選的成員自動完成](media/code-editing-completion-filtering.png)

當您在變數或值之後輸入句點時，會自動顯示成員自動完成內容，並顯示可能類型的方法和屬性。 如果某個變數可以是多個類型，此清單會包含所有類型的所有可能值，以及指出哪些類型支援每項自動完成的額外資訊。 當所有可能的類型都支援自動完成時，將顯示為無註解。

![多個類型時的成員自動完成](media/code-editing-completion-types.png)

預設不顯示 "dunder" 成員 (開頭和結尾是雙底線的成員)。 一般情況下，這類成員應該不能直接存取。 但如果您需要這樣的成員，輸入前置雙底線就會將這些自動完成的內容新增至清單：

![私用成員自動完成](media/code-editing-completion-dunder.png)

`import` 和 `from ... import` 陳述式會顯示一份可以匯入的模組清單。 使用 `from ... import`，該清單就會包括可從指定模組匯入的成員。

![匯入自動完成](media/code-editing-completion-import.png)

`raise` 和 `except` 陳述式會顯示一份可能錯誤類型的類別清單。 該清單可能不包含所有使用者定義的例外狀況，但會協助您快速尋找適合的內建例外狀況︰

![例外狀況自動完成](media/code-editing-completion-exception.png)

輸入 @ 會啟動裝飾項目，並顯示可能的裝飾項目。 其中的許多項目無法用為裝飾項目，請參考程式庫文件決定要使用何者。

![裝飾項目自動完成](media/code-editing-completion-decorator.png)

> [!Tip]
> 您可以透過 [工具] > [選項] > [文字編輯器] > [Python] > [進階] 來設定自動完成的行為。 其中，[依據搜尋字串篩選清單]︰在您輸入時套用自動完成建議的篩選 (預設為核取)，而 [成員自動完成顯示成員的交集] 只會顯示所有可能的類型支援的自動完成 (預設為未核取)。 請參閱[選項 - 完成結果](python-support-options-and-settings-in-visual-studio.md#completion-results)。

### <a name="signature-help"></a>簽章說明

撰寫呼叫函式的程式碼時，簽章說明會在您輸入左側 `(` 時顯示，並顯示可用的文件和參數資訊。 您也可使用 Ctrl + Shift + 空格鍵，讓它出現在函式呼叫中。 顯示的資訊取決於函式的原始程式碼中的文件字串，但會包括任何預設值。

![簽章說明](media/code-editing-signature-help.png)

> [!Tip]
> 若要停用簽章說明，請移至 [工具] > [選項] > [文字編輯器] > [Python] > [一般]，然後清除 [陳述式完成] > [參數資訊]。

### <a name="quick-info"></a>快速諮詢

將滑鼠指標停留在識別項會顯示快速諮詢工具提示。 依識別項而定，快速諮詢可能會顯示可能的值或類型、任何可用的文件、傳回類型和定義位置︰

![快速諮詢](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>程式碼著色

程式碼著色使用程式碼分析中的資訊，將變數、陳述式及您的程式碼的其他部分著色。 例如，參考模組或類別的變數可能會以不同於函式或其他值的色彩顯示，參數名稱可能會以不同於本機或全域變數的色彩顯示。 (根據預設，函式不會以粗體顯示)：

![程式碼著色](media/code-editing-code-coloring.png)

若要自訂色彩，請移至 [工具] > [選項] > [環境] > [字型和色彩]，並修改 [顯示項目] 清單中的 Python 項目：

![字型與色彩選項](media/code-editing-customize-colors.png)

> [!Tip]
> 若要停用程式碼著色，請移至 [工具] > [選項] > [文字編輯器] > [Python] > [進階]，清除 [其他選項] > [根據類型為名稱著色]。 請參閱[選項 - 其他選項](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)。

## <a name="code-snippets"></a>程式碼片段

程式碼片段是一個片段的程式碼，可透過輸入捷徑並按 Tab 或使用 [編輯] > [IntelliSense] > [插入程式碼片段範圍陳述式]  命令插入到檔案。 例如，在 Tab 鍵之後輸入 `class` 會產生類別的其餘部分。 您可以在名稱和基底清單上輸入、使用 Tab 在反白顯示的欄位之間移動，然後按 Enter 開始輸入主體。

![程式碼片段](media/code-editing-code-snippets.png)

您可以在 [程式碼片段管理員] 中看到可用的程式碼片段 ([工具] > [程式碼片段管理員])，選取 [Python] 做為語言︰

![程式碼片段管理員](media/code-editing-code-snippets-manager.png)

若要建立您自己的程式碼片段，請參閱[逐步解說︰建立程式碼片段 (英文)](../ide/walkthrough-creating-a-code-snippet.md)。 

如果您寫了出色的程式碼片段並想與人分享，請隨意張貼在 Gist 中並[聯絡我們](https://github.com/Microsoft/PTVS/issues)。 也許我們在未來的 Visual Studio 版本中可以納入這些片段。

## <a name="navigating-your-code"></a>巡覽程式碼

Visual Studio 中的 Python 支援提供幾種快速瀏覽程式碼 (以及有提供原始程式碼的程式庫) 的方式︰[瀏覽列](#navigation-bar)、[移至定義](#go-to-definition)、[巡覽至](#navigate-to)以及[尋找所有參考](#find-all-references)。 您也可以使用 Visual Studio 的[物件瀏覽器](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)。

### <a name="navigation-bar"></a>巡覽列

導覽列會顯示在每個編輯器視窗頂端，並包含兩個層級的定義清單。 左邊的下拉式清單包含目前檔案中最上層的類別和函式定義；右邊的下拉式清單會在左邊的範圍內顯示定義清單。 當您在編輯器中移動時，這些清單會更新以顯示您目前的內容，您也可以從這些清單中選取一個項目以直接跳至該處。

![巡覽列](media/code-editing-navigation-bar.png)

> [!Tip]
> 若要隱藏導覽列，請移至 [工具] > [選項] > [文字編輯器] > [Python] > [一般]，並清除 [設定] > [導覽列]。

### <a name="go-to-definition"></a>移至定義

[移至定義] 可從使用的識別項 (例如函式名稱、類別或變數) 快速跳至定義原始程式碼的位置。 若要叫用 [移至定義]，請以滑鼠右鍵按一下某個識別碼，然後選取 [移至定義]，或將插入點放在識別碼並按 F12。 它適用於您的程式碼和提供原始程式碼的外部程式庫。 如果沒有程式庫原始程式碼，[移至定義] 會跳至模組參考的相關 `import` 陳述式，或是顯示錯誤。

![移至定義](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>巡覽至

[編輯] > [巡覽至] 命令 (Ctrl + 逗點) 會在編輯器中顯示搜尋方塊，您可在其中輸入任何字串，並在定義函式、類別或包含該字串之變數的程式碼中看到可能的相符項目。 此功能提供與 [移至定義] 類似的功能，但不需尋找使用的識別碼。

按兩下任一名稱，或使用方向鍵選取並按 Enter，即可瀏覽至該識別項的定義。

![巡覽至](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>尋找所有參考

[尋找所有參考] 是探索在何處同時定義和使用 (包括匯入和指派) 任一指定識別項的有用方式。 要叫用 [尋找所有參考]，請以滑鼠右鍵按一下某個識別項，然後選取 [尋找所有參考]，或將插入點放在識別項中並按 Shift+F12。 按兩下清單中的項目會巡覽至其位置。

![[尋找所有參考] 結果](media/code-editing-find-all-references.png)

## <a name="see-also"></a>另請參閱

- [格式設定](formatting-python-code.md)
- [重構](refactoring-python-code.md)
- [正在 Lint](linting-python-code.md)