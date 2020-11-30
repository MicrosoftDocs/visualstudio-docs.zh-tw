---
title: 動態符號執行 | Microsoft IntelliTest 開發人員測試工具
description: 瞭解 IntelliTest 如何藉由分析程式中的分支條件來產生參數化單元測試的輸入。
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 771fd167a2dc9fce8278ca53f730872a9f170eb7
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329906"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>使用動態符號執行產生輸入

IntelliTest 會藉由分析程式中的分支條件，以產生[參數化單元測試](test-generation.md#parameterized-unit-testing)的輸入。 測試輸入是根據它們是否可觸發程式的新分支行為進行選擇。 分析是一種累加的處理序。 它會修改正式測試輸入參數 `I` 的述詞 `q: I -> {true, false}`。 `q` 表示 IntelliTest 已觀察的一組行為。 一開始 `q := false`，因為尚未觀察到任何項目。

迴圈的步驟如下：

1. IntelliTest 會使用[條件約束規劃求解](#constraint-solver)決定輸入 `i`，使得 `q(i)=false`。 透過建構，輸入 `i` 就會採用之前未看過的執行路徑。 一開始，這表示 `i` 可以是任何輸入，因為沒有尚未探索到的執行路徑。

1. IntelliTest 會以所選的輸入 `i` 執行測試，並監視測試和待測程式的執行狀況。

1. 在執行期間，程式會採用程式的所有條件式分支所判定的特定路徑。 判定執行的所有條件集合稱為「路徑條件」，撰寫為正式輸入參數的述詞 `p: I -> {true, false}`。 IntelliTest 會計算這個述詞的表示法。

1. IntelliTest 會設定 `q := (q or p)`。 換句話說，它記錄了已看到 `p` 所代表路徑的事實。

1. 移至步驟 1。

IntelliTest 的[條件約束規劃求解](#constraint-solver)可處理 .NET 程式中可能出現的所有類型值：

* [整數](#integers-and-floats)和[浮點數](#integers-and-floats)
* [物件](#objects)
* [結構](#structs)
* [陣列](#arrays-and-strings) 和 [字串](#arrays-and-strings)

IntelliTest 會篩選掉違反規定假設的輸入。

除了即時輸入 ([參數化單元測試](test-generation.md#parameterized-unit-testing)的引數) 外，測試還可以從 [PexChoose](static-helper-classes.md#pexchoose) 靜態類別提取進一步的輸入值。 這些選擇也決定了[參數化模擬](#parameterized-mocks)的行為。

## <a name="constraint-solver"></a>條件約束規劃求解

IntelliTest 會使用條件約束規劃求解來判定測試和待測程式的相關輸入值。

IntelliTest 使用 [Z3](https://github.com/Z3Prover/z3/wiki) 條件約束規劃求解。

## <a name="dynamic-code-coverage"></a>動態程式碼涵蓋範圍

作為執行階段監視的副作用，IntelliTest 會收集動態程式碼涵蓋範圍資料。
這稱為「動態」的原因是 IntelliTest 只知道已執行的程式碼，因此它無法以其他涵蓋範圍工具通常使用的相同方式，提供涵蓋範圍的絕對值。

例如，當 IntelliTest 報告動態涵蓋範圍為 5/10 基本區塊時，這表示已涵蓋十個中的五個區塊，其中分析到目前為止已觸達之所有方法 (相對於待測組件中已存在的所有方法) 的區塊總數是十個。
稍後在分析中，隨著探索到更多的可觸達方法，分子 (在此範例中為 5) 和分母 (10) 都可能會增加。

## <a name="integers-and-floats"></a>整數和浮點數

IntelliTest 的 [條件約束規劃求解](#constraint-solver)可決定基本類型的測試輸入值 (例如 **byte**、**int**、**float** 等等)，以觸發測試和待測程式的不同執行路徑。

## <a name="objects"></a>物件

IntelliTest 可以[建立現有 .NET 類別的執行個體](#existing-classes)，或者您可以使用 IntelliTest 來自動[建立模擬物件](#parameterized-mocks)，以實作特定介面，並根據用途以不同的方式運作。

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>具現化現有類別

**怎麼了？**

IntelliTest 在執行測試和待測程式時，會監視已執行的指令。 特別是，它會監視對欄位的所有存取。 然後，它會使用[條件約束規劃求解](#constraint-solver)來判定新的測試輸入 (包括物件和其欄位值)，使得測試和待測程式以其他相關方式表現。

這表示 IntelliTest 必須建立特定類型的物件，並設定其欄位值。 如果類別為[可見](#visibility)且具有[可見](#visibility)的預設建構函式，IntelliTest 可建立類別的執行個體。
如果類別的所有欄位都為[可見](#visibility)，IntelliTest 可自動設定欄位。

如果類型不可見或欄位不[可見](#visibility)，IntelliTest 需要協助建立物件，並使其進入相關狀態，以達到最大的程式碼涵蓋範圍。 IntelliTest 可使用反映來以任意方式建立和初始化執行個體，但這通常不可取，因為它可能會使物件進入正常程式執行期間可能永遠不會發生的狀態。 相反地，IntelliTest 會依賴來自使用者的提示。

## <a name="visibility"></a>可見度

.NET 中有一個詳盡的可見性模型：類型、方法、欄位和其他成員可以是 **私人**、**公用**、**內部** 等等。

當 IntelliTest 產生測試時，它只會嘗試執行所產生測試內容中 .NET 可見性規則的合法動作 (例如呼叫建構函式、方法和設定欄位)。

規則如下︰

* **內部成員的可見性**
  * IntelliTest 假設所產生的測試可以存取封入 [PexClass](attribute-glossary.md#pexclass) 可見的內部成員。
  .NET 有 **InternalsVisibleToAttribute** 可將內部成員的可見性延伸到其他組件。

* **[PexClass](attribute-glossary.md#pexclass) 的私人和家庭 (在 C# 中為受保護) 成員的可見性**
  * IntelliTest 一律會將產生的測試直接放入 [PexClass](attribute-glossary.md#pexclass) 或子類別中。 因此，IntelliTest 假設它可能會使用所有可見的家庭成員 (在 C# 中為 **受保護**)。
  * 如果產生的測試直接放入 [PexClass](attribute-glossary.md#pexclass) 中(通常是透過使用部分類別)，IntelliTest 會假設它也可以使用 [PexClass](attribute-glossary.md#pexclass) 的所有私人成員。

* **公用成員的可見性**
  * IntelliTest 假設它可能會使用 [PexClass](attribute-glossary.md#pexclass) 內容中可見的所有已匯出成員。

## <a name="parameterized-mocks"></a>參數化模擬

如何測試具有介面類型參數的方法？ 或是具有非密封類別參數的方法？ IntelliTest 不知道在呼叫這個方法時，稍後將使用的實作。 而且也許在測試時甚至沒有可用的實際實作。

傳統的解決方法是使用具有明確行為的「模擬物件」。

一個模擬物件可實作一個介面 (或延伸非密封類別)。 它不代表實際的實作，而只是允許使用模擬物件執行測試的捷徑。 其行為是根據每個使用它的測試案例，以手動方式定義。 有許多工具可讓您輕鬆地定義模擬物件和其預期的行為，但這種行為仍然必須以手動方式定義。

IntelliTest 可以產生值來替代模擬物件中的硬式編碼值。 就像它啟用了[參數化單元測試](test-generation.md#parameterized-unit-testing)一樣，IntelliTest 也會啟用參數化模擬。

參數化模擬有兩種不同的執行模式：

* **選擇**：探索程式碼時，參數化模擬是其他測試輸入的來源，IntelliTest 將嘗試選擇相關值
* **重新執行**：執行先前產生的測試時，參數化模擬的表現與虛設常式的行為 (換句話說，預先定義的行為) 相同。

請使用 [PexChoose](static-helper-classes.md#pexchoose) 來取得參數化模擬的值。

## <a name="structs"></a>結構

IntelliTest 對 **結構** 值的推理類似於其處理 [物件](#objects)的方式。

## <a name="arrays-and-strings"></a>陣列和字串

IntelliTest 在執行測試和待測程式時，會監視已執行的指令。 特別是，它觀察到程式何時相依於字串或陣列的長度 (以及多維陣列的下限和長度)。
還觀察到程式如何使用不同的字串或陣列元素。 然後，它會使用[條件約束規劃求解](#constraint-solver)，判定哪些長度和元素值可能會造成測試和待測程式以相關方式表現。

IntelliTest 會嘗試將觸發相關程式行為所需的陣列和字串大小降到最低。

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>取得其他輸入

[PexChoose](static-helper-classes.md#pexchoose) 靜態類別可用來取得其他測試輸入，而且可用來實作[參數化模擬](#parameterized-mocks)。

## <a name="got-feedback"></a>有人給您意見嗎？

在[開發人員社群](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)上張貼您的意見與功能建議。

## <a name="further-reading"></a>進一步閱讀

* [運作方式](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
