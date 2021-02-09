---
title: 編輯 Python 程式碼
description: 對於 Python，Visual Studio 可提供豐富的 IntelliSense、程式碼片段及導覽功能，還有格式設定、Linting 和重構。
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fa0caa8184f3c52a010df1dd1f82718d44be700b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888052"
---
# <a name="edit-python-code"></a>編輯 Python 程式碼

因為您大部分的開發時間都花在程式碼編輯器中，所以 [Visual Studio 中的 Python 支援](installing-python-support-in-visual-studio.md)提供的功能可協助您提高生產力。 功能包括了 IntelliSense 語法反白顯示、自動完成、簽章說明、方法覆寫、搜尋和瀏覽。

編輯器也會與 Visual Studio 中的 **互動式** 視窗整合，讓您輕鬆地在兩者間交換程式碼。 如需詳細資訊，請參閱[教學課程步驟 3：使用互動式 REPL 視窗](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)和[使用互動式視窗 - 傳送至互動式命令](python-interactive-repl-in-visual-studio.md#send-to-interactive-command)。

如需有關在 Visual Studio 中編輯程式碼的一般文件，請參閱[程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)。 另請參閱[大綱](../ide/outlining.md)，這有助您專注於特定的程式碼區段。

您也可以使用 Visual Studio [物件瀏覽器] ([檢視] > [其他視窗] > [物件瀏覽器] 或 **Ctrl**+**W** > **J**) 來檢查每個模組中定義的 Python 類別，以及這些類別中定義的函式。

## <a name="intellisense"></a>IntelliSense

IntelliSense 提供[自動完成](#completions)、[簽章說明](#signature-help)、[快速諮詢](#quick-info)和[程式碼著色](#code-coloring)。 Visual Studio 2017 15.7 版和更新版本也支援[類型提示](#type-hints)。

為了改善效能，Visual Studio 2017 15.5 版及較舊版本中之 IntelliSense 會仰賴為您專案中每個 Python 環境所產生的完成資料庫。 如果新增、移除或更新套件，資料庫可能需要重新整理。 資料庫狀態會顯示在 [ **Python 環境**] 視窗中 ([ **IntelliSense** ] 索引標籤上 **方案總管**) 的同級 (查看 [環境視窗參考](python-environments-window-tab-reference.md)) 。

Visual Studio 2017 15.6 版及更新版本會使用不同的方式，在不仰賴資料庫的情況下為 IntelliSense 提供完成。

### <a name="completions"></a>自動完成

自動完成會顯示為陳述式、識別碼和其他適合在編輯器目前的位置中輸入的文字。 清單中顯示的資訊會以內容為依據，並會經過篩選以省略不正確或令人分心的選項。 完成通常是藉由輸入不同的語句 (例如 `import`) 和運算子 (包含句點) 來觸發，但您可以隨時輸入 **Ctrl**# +   >  **空格鍵** 來顯示它們。

![Visual Studio 編輯器中的成員自動完成](media/code-editing-completions-simple.png)

自動完成清單開啟後，您可以使用方向鍵、滑鼠來搜尋您想要的自動完成內容，或是繼續輸入。 隨著您輸入更多字元，清單會進一步篩選以顯示可能的自動完成內容。 您也可以使用快速鍵，例如：

- 輸入不在名稱開頭的字母，例如，輸入 'parse' 以尋找 'argparse'
- 只輸入每個字組開頭的字母，例如，輸入 'abc' 以尋找 'AbstractBaseClass'，或輸入 'air' 以尋找 'as_integer_ratio'
- 略過字母 (例如 'b64') 以尋找 'base64'

以下是一些範例：

![Visual Studio 編輯器中具篩選的成員自動完成](media/code-editing-completion-filtering.png)

當您在變數或值之後鍵入句點時，會自動顯示成員自動完成內容，並顯示可能類型的方法和屬性。 如果某個變數可以是多個類型，此清單會包含所有類型的所有可能值，以及指出哪些類型支援每項自動完成的額外資訊。 當所有可能的類型都支援自動完成時，將顯示為無註解。

![Visual Studio 編輯器中多個類型時的成員自動完成](media/code-editing-completion-types.png)

預設不顯示 "dunder" 成員 (開頭和結尾是雙底線的成員)。 一般情況下，這類成員應該不能直接存取。 但如果您需要這樣的成員，鍵入前置雙底線就會將這些自動完成的內容新增至清單：

![Visual Studio 編輯器中的私人成員自動完成](media/code-editing-completion-dunder.png)

`import` 和 `from ... import` 陳述式會顯示一份可以匯入的模組清單。 使用 `from ... import`，該清單就會包括可從指定模組匯入的成員。

![Visual Studio 編輯器中的匯入自動完成](media/code-editing-completion-import.png)

`raise` 和 `except` 陳述式會顯示一份可能錯誤類型的類別清單。 該清單可能不包含所有使用者定義的例外狀況，但會協助您快速尋找適合的內建例外狀況︰

![Visual Studio 編輯器中的例外狀況自動完成](media/code-editing-completion-exception.png)

輸入 @ 會啟動裝飾項目，並顯示可能的裝飾項目。 其中的許多項目無法用為裝飾項目，請參考程式庫文件決定要使用何者。

![Visual Studio 編輯器中的裝飾項目自動完成](media/code-editing-completion-decorator.png)

> [!Tip]
> 您可以透過 **工具**  >  **選項**  >  **文字編輯器**  >  **Python**  >  **Advanced** 來設定完成的行為。 其中，[依據搜尋字串篩選清單] 會在您鍵入時套用自動完成建議的篩選 (預設為核取)，而 [成員自動完成顯示成員的交集] 只會顯示所有可能的類型支援的自動完成 (預設為未核取)。 請參閱[選項 - 完成結果](python-support-options-and-settings-in-visual-studio.md#completion-results)。

### <a name="type-hints"></a>類型提示

*Visual Studio 2017 15.7 版和更新版本。*

Python 3.5 以上版本 ([PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org) 中的「類型提示」是表示引數類型、傳回值和類別屬性的函式和類別的註釋語法。 當您將滑鼠停留在具有這些註釋的函式呼叫、引數和變數上方時，IntelliSense 就會顯示類型提示。

在下列範例中，`Vector` 類別會宣告為 `List[float]`，而 `scale` 函式包含其引數和傳回值的類型提示。 將滑鼠停留在該函式呼叫上方即會顯示類型提示：

![將滑鼠停留函式呼叫上方來顯示類型提示](media/code-editing-type-hints1.png)

在下列範例中，您可以看到 `Employee` 類別的標註屬性如何顯示在屬性的 IntelliSense 完成快顯視窗中：

![顯示類型提示的 IntelliSense 完成](media/code-editing-type-hints2.png)

在整個專案中驗證類型提示也很有用，因為通常要到執行階段之後才會出現錯誤。 基於此目的，Visual Studio 會在方案總管中透過內容功能表命令 **Python**  >  **執行 MyPy** 來整合產業標準MyPy 工具：

![在 [方案總管] 執行 MyPy 操作功能表命令](media/code-editing-type-hints-run-mypy.png)

必要的話，執行命令會提示您安裝 mypy 套件。 Visual Studio 接著會執行 mypy 來驗證專案中每個 Python 檔案的類型提示。 錯誤會顯示在 Visual Studio 的 [錯誤清單] 視窗中。 在視窗中選取項目會巡覽至程式碼中的適當行。

簡單舉例如下，下列函式定義包含類型提示，指出 `input` 引數是類型 `str`，而該函式的呼叫會嘗試傳遞整數：

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

對這段程式碼使用 [執行 Mypy] 命令會產生下列錯誤：

![mypy 驗證類型提示的範例結果](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> 如果是 3.5 之前的 Python 版本，Visual Studio 也會顯示您透過「Typeshed 虛設常式檔案」 (*.pyi*) 提供的類型提示。 只要您不想在程式碼中直接包含類型提示，或者您想要針對不會直接使用類型提示的程式庫建立類型提示時，就可以使用虛設常式檔案。 如需詳細資訊，請參閱 mypy 專案 Wiki 中的 [Create stubs for Python modules](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) (建立 Python 模組的虛設常式)。
>
> 目前，Visual Studio 不支援註解的類型提示。
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> 如果是 3.5 之前的 Python 版本，Visual Studio 也會顯示您透過「Typeshed 虛設常式檔案」 (*.pyi*) 提供的類型提示。 只要您不想在程式碼中直接包含類型提示，或者您想要針對不會直接使用類型提示的程式庫建立類型提示時，就可以使用虛設常式檔案。 如需詳細資訊，請參閱 mypy 專案 Wiki 中的 [Create stubs for Python modules](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) (建立 Python 模組的虛設常式)。
>
> Visual Studio 包括一組 Python 2 和 3，的配套 Typeshed 檔案，因此不需要下載其他項目。 但是，如果您想要使用一組不同的檔案，您可以在 [**工具**  >  **選項**  >  **Python**  >  **語言伺服器** 選項] 中指定路徑。 請參閱[選項 - 語言伺服器](python-support-options-and-settings-in-visual-studio.md#language-server-options)。
>
> 目前，Visual Studio 不支援註解的類型提示。
::: moniker-end

### <a name="signature-help"></a>簽章說明

撰寫呼叫函式的程式碼時，簽章說明會在您鍵入左側 `(` 時顯示，並顯示可用的文件和參數資訊。 您也可以在 +  + 函式呼叫內以 Ctrl Shift **空格鍵** 來顯示它。 顯示的資訊取決於函式的原始程式碼中的文件字串，但會包括任何預設值。

![Visual Studio 編輯器中的簽章說明](media/code-editing-signature-help.png)

> [!Tip]
> 若要停用簽章說明，請移至 [**工具**  >  **選項**  >  **文字編輯器**  >  **Python**  >  **一般**] 和 [清除 **語句完成**  >  **參數資訊**]。

### <a name="quick-info"></a>快速諮詢

將滑鼠指標停留在識別項會顯示快速諮詢工具提示。 依識別項而定，快速諮詢可能會顯示可能的值或類型、任何可用的文件、傳回型別和定義位置：

![Visual Studio 編輯器中的快速諮詢](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>程式碼著色

程式碼著色使用程式碼分析中的資訊，將變數、陳述式及您的程式碼的其他部分著色。 例如，參考模組或類別的變數可能會以不同於函式或其他值的色彩顯示，參數名稱可能會以不同於本機或全域變數的色彩顯示。 (根據預設，函式不會以粗體顯示)：

![程式碼和 Visual Studio 編輯器中的語法著色](media/code-editing-code-coloring.png)

若要自訂色彩，請移至 [**工具**  >  **選項**  >  **環境** 字型  >  **和色彩**]，並修改 [**顯示專案**] 清單中的 **Python** 專案：

![Visual Studio 中的字型和色彩選項](media/code-editing-customize-colors.png)

> [!Tip]
> 若要停用程式碼著色，請移至 **工具**  >  **選項**  >  **文字編輯器**  >  **Python**  >  **Advanced** ，並根據類型清除 **其他選項**  >  **色彩名稱**。 請參閱[選項 - 其他選項](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)。

## <a name="code-snippets"></a>程式碼片段

程式碼片段是一個片段的程式碼，可透過鍵入捷徑並按 **Tab** 鍵，或是使用 [編輯] > [IntelliSense] > [插入程式碼片段] 及 [以此環繞] 命令，選取 [Python]，然後選取所需的程式碼片段來插入到檔案。

例如，`class` 為插入類別定義之程式碼片段的捷徑。 您會在輸入 `class` 時，於自動完成清單中看見該程式碼片段：

![適用於類別捷徑的程式碼片段](media/code-editing-code-snippet-class.png)

按 **Tab 鍵** 會產生類別的其餘部分。 然後，您可以在名稱和基底清單上輸入，在反白顯示的欄位之間 **移動，然後** 按 **enter** 鍵以開始鍵入本文。

![反白顯示待完成的程式碼片段區域](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>功能表命令

當您使用 [**編輯**  >  **IntelliSense**  >  **插入程式碼片段**] 功能表命令時，請先選取 [ **Python**]，然後選取程式碼片段：

![透過 [插入程式碼片段] 命令選取程式碼片段](media/code-editing-code-snippet-insert.png)

**編輯**  >  **IntelliSense**  >  **以命令括住**，同樣地，會將目前的選取專案置於文字編輯器中所選的結構元素內。 例如，假設您有類似以下的程式碼：

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

選取此程式碼並選取 [以此環繞] 命令，將會顯示可用程式碼片段清單。 從清單中選擇 **def** 會將選取的程式碼置於函式定義內，且您可以使用 **Tab** 鍵來在反白顯示的函式名稱及引數之間巡覽：

![針對程式碼片段使用 [以此環繞] 命令](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>檢查可用的程式碼片段

您可以在 [程式碼片段管理員] 中查看可用的程式碼片段。[程式碼片段管理員] 的開啟方式為使用 [工具] > [程式碼片段管理員] 功能表命令，並選取 [Python] 作為語言：

![Visual Studio 中的程式碼片段管理員](media/code-editing-code-snippets-manager.png)

若要建立您自己的程式碼片段，請參閱[逐步解說︰建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)。

如果您寫了出色的程式碼片段並想與人分享，請隨意張貼在 Gist 中並[聯絡我們](https://github.com/Microsoft/PTVS/issues)。 也許我們在未來的 Visual Studio 版本中可以納入這些片段。

## <a name="navigate-your-code"></a>巡覽您的程式碼

Visual Studio 中的 Python 支援提供幾種快速巡覽程式碼 (以及有提供原始程式碼的程式庫) 的方式︰[導覽列](#navigation-bar)、[**移至定義**](#go-to-definition)、[**巡覽至**](#navigate-to)以及 [**尋找所有參考**](#find-all-references)。 您也可以使用 Visual Studio 的 [[物件瀏覽器]](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)。

### <a name="navigation-bar"></a>導覽列

導覽列會顯示在每個編輯器視窗頂端，並包含兩個層級的定義清單。 左邊的下拉式清單包含目前檔案中最上層的類別和函式定義；右邊的下拉式清單會在左邊的範圍內顯示定義清單。 當您在編輯器中移動時，這些清單會更新以顯示您目前的內容，您也可以從這些清單中選取一個項目以直接跳至該處。

![Visual Studio 編輯器中的導覽列](media/code-editing-navigation-bar.png)

> [!Tip]
> 若要隱藏巡覽列，請移至 [**工具**  >  **選項**  >  **文字編輯器**  >  **Python**  >  **一般**] 和 [清除 **設定**]  >  **巡覽列**。

### <a name="go-to-definition"></a>移至定義

[移至定義] 可從使用的識別項 (例如函式名稱、類別或變數) 快速跳至定義原始程式碼的位置。 若要叫用 [移至定義]，請以滑鼠右鍵按一下某個識別項，然後選取 [移至定義]，或將插入點放在識別項並按 **F12** 鍵。 它適用於您的程式碼和提供原始程式碼的外部程式庫。 如果沒有程式庫原始程式碼，[移至定義] 會跳至模組參考的相關 `import` 陳述式，或是顯示錯誤。

![Visual Studio 中的 [移至定義] 命令](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>巡覽至

[**編輯**  >  **流覽至**] 命令 (**Ctrl** + **，**) 在編輯器中顯示搜尋方塊，您可以在編輯器中輸入任何字串，並在您的程式碼中查看可定義包含該字串之函式、類別或變數的可能相符專案。 此功能提供與 [移至定義] 類似的功能，但不需尋找使用的識別碼。

按兩下任一名稱，或使用方向鍵選取並按 **Enter** 鍵，即可巡覽至該識別項的定義。

![Visual Studio 中的 [巡覽至] 命令](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>尋找所有參考

[尋找所有參考] 是探索在何處同時定義和使用 (包括匯入和指派) 任一指定識別項的有用方式。 若要叫用 [尋找所有參考]，請以滑鼠右鍵按一下某個識別項，然後選取 [尋找所有參考]，或將插入點放在識別項中並按 **Shift**+**F12**。 按兩下清單中的項目會巡覽至其位置。

![[尋找所有參考] 結果](media/code-editing-find-all-references.png)

## <a name="see-also"></a>另請參閱

- [格式設定](formatting-python-code.md)
- [重構](refactoring-python-code.md)
- [使用 Linter](linting-python-code.md)
