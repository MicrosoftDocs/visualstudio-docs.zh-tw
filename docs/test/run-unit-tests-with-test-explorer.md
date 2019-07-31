---
title: 使用 [測試總管] 執行單元測試並進行偵錯
description: 了解如何在 Visual Studio 中使用 [測試總管] 執行測試。 本主題涵蓋如何在建置後啟用自動測試回合、檢視測試結果、群組和篩選測試清單、建立播放清單、偵錯測試，以及使用測試捷徑。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68ed41eeecde853459bc9c817d84bd433788084c
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493306"
---
# <a name="run-unit-tests-with-test-explorer"></a>使用測試總管執行單元測試

使用 [測試總管]  從 Visual Studio 或協力廠商單元測試專案中執行單元測試。 您也可以使用 [測試總管]  將測試分組成分類、篩選測試清單，以及建立、儲存和執行測試播放清單。 您可以偵錯測試和分析測試效能和程式碼涵蓋範圍。

Visual Studio 2015 包含 Managed 程式碼和機器碼皆適用的 Microsoft 單元測試架構。 不過，[測試總管]  也可以執行任何已實作測試總管配接器的單元測試架構。 如需安裝協力廠商單元測試架構的詳細資訊，請參閱[安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)。

[測試總管]  可以從解決方案中的多個測試專案來執行測試，以及從屬於實際執行程式碼專案的測試類別來執行測試。 測試專案可以使用不同的單元測試架構。 當進行測試的程式碼是為 .NET 撰寫時，測試專案可以用任何同樣以 .NET 為目標的語言撰寫，而不管目標程式碼的語言為何。 原生 C/C++ 程式碼專案必須使用 C++ 單元測試架構進行測試。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)。

## <a name="run-tests-in-test-explorer"></a>在 [測試總管] 中執行測試

在建置測試專案後，這些測試便會出現在 [測試總管] 中。 如果沒有看到 [測試總管]，請選擇 Visual Studio 功能表上的 [測試]  ，接著選擇 [Windows]  ，然後選擇 [測試總管]  。

![測試總管](../test/media/ute_failedpassednotrunsummary.png)

當您執行、寫入、重新執行您的測試時，測試總管會顯示 [失敗的測試]  、[通過的測試]  、[略過的測試]  和 [未執行的測試]  預設群組中的結果。 您可以變更測試總管群組測試的方式。

您可以從 [測試總管]  工具列，執行尋找、組織及執行測試等許多工作。

![從 [測試總管] 的工具列執行測試](../test/media/ute_toolbar.png)

### <a name="run-tests"></a>執行測試

您可以執行方案中的所有測試、群組中的所有測試，或是您選取的一組測試。 執行下列任一步驟：

- 若要執行方案中的所有測試，請選擇 [全部執行]  。

- 若要執行預設群組中的所有測試，請選擇 [執行]  ，然後選擇功能表上的群組。

- 選取您要執行的個別測試、開啟所選取之測試的右鍵功能表，然後選擇 [執行選取的測試]  。

- 如果個別測試沒有任何會防止它們依任意順序執行的相依性，請使用工具列上的 ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) 切換按鈕開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。

執行測試時，[測試總管]  視窗頂端會動畫呈現**成功/失敗列**。 測試回合結束時，如果所有測試皆成功，**成功/失敗列**會變成綠色；如果有任何一個測試失敗，則會變成紅色。

### <a name="run-tests-after-every-build"></a>每次建置後執行測試

|按鈕|說明|
|-|-|
|![建置後執行](../test/media/ute_runafterbuild_btn.png)|若要在每次本機建置之後執行單元測試，請在標準功能表中選擇 [測試]  ，然後選擇 [測試總管]  工具列上的 [建置之後執行測試]  。|

> [!NOTE]
> 若要在每次建置後執行單元測試，必須具備 Visual Studio 2017 Enterprise 或 Visual Studio 2019。 Visual Studio 2019 的 Community、Professional 和 Enterprise 版均隨附此功能。

## <a name="view-test-results"></a>檢視測試結果

當您執行、寫入、重新執行您的測試時，測試總管會顯示 [失敗的測試]  、[通過的測試]  、[略過的測試]  和 [未執行的測試]  群組中的結果。 在測試總管底部的詳細資料窗格會顯示測試回合的摘要。

### <a name="view-test-details"></a>檢視測試詳細資料

若要檢視個別測試的詳細資料，請選取該測試。

![測試執行詳細資料](../test/media/ute_testdetails.png)

測試詳細資料窗格會顯示下列資訊：

- 測試方法的原始檔案名稱和行號。

- 測試的狀態。

- 測試方法執行的經過時間。

如果測試失敗，詳細資料窗格也會顯示：

- 測試的單元測試架構所傳回的訊息。

- 測試失敗時的堆疊追蹤。

### <a name="view-the-source-code-of-a-test-method"></a>檢視測試方法的原始程式碼

若要在 Visual Studio 編輯器中顯示測試方法的原始程式碼，請選取測試，然後選擇右鍵功能表上的 [開啟測試]  (鍵盤：**F12**)。

## <a name="group-and-filter-the-test-list"></a>群組和篩選測試清單

測試總管可讓您將測試分組到預先定義的分類。 在測試總管中執行的大部分單元測試架構可讓您定義自己的分類和分類/值組來群組您的測試。 您也可以透過比對字串和測試屬性來篩選測試清單。

### <a name="group-tests-in-the-test-list"></a>將測試清單中的測試分組

若要變更測試的組織方式，請選擇 [群組依據]  按鈕 ![測試總管的 [群組] 按鈕](../test/media/ute_groupby_btn.png)旁邊的向下箭號，然後選取新的分組準則。

![在 [測試總管] 中依分類為測試分組](../test/media/ute_groupbycategory.png)

### <a name="test-explorer-groups"></a>測試總管群組

|群組|說明|
|-|-----------------|
|**持續期間**|依據執行時間群組測試：[快]  、[中]  和 [慢]  。|
|**結果**|依據執行結果群組測試：[失敗的測試]  、[略過的測試]  、[成功的測試]  。|
|**特性**|依據您定義的分類/值組群組測試。 指定特性分類和值的語法是由單元測試架構所定義。|
|**專案**|依據名稱專案群組測試。|

### <a name="group-by-traits"></a>依據特性群組

特性通常是分類名稱/值組，但也可以是單一分類。 您可將特性指派給方法，其中單元測試架構可將其識別為測試方法。 單元測試架構可以定義特性分類。 您可以將值加入特性分類以定義自己的分類名稱/值組。 指定特性分類和值的語法是由單元測試架構所定義。

**Microsoft Managed 程式碼單元測試架構中的特性**

Microsoft Managed 程式碼單元測試架構中，您可在  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> 屬性中定義特性名稱/值組。 測試架構也包含下列預先定義的特性：

|特性|說明|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|擁有者分類是由單元測試架構所定義，會要求您提供擁有者的字串值。|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|優先權分類是由單元測試架構所定義，會要求您提供優先權的整數值。|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory 屬性可讓您提供沒有值的分類。 TestCategory 屬性定義的分類也可以是 TestProperty 屬性的分類。|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty 屬性可讓您定義特性分類/值組。|

**Microsoft C++ 單元測試架構中的特性**

 請參閱[如何使用適用於 C++ 的 Microsoft 單元測試架構](how-to-use-microsoft-test-framework-for-cpp.md)。

### <a name="search-and-filter-the-test-list"></a>搜尋和篩選測試清單

您可以使用測試總管篩選條件，以在檢視和執行的專案中限制測試方法。

當您在 [測試總管]  的搜尋方塊鍵入字串並選擇 **Enter** 時，會將測試清單篩選為只顯示包含該字串之完整名稱的測試。

若要依據不同準則篩選：

1. 開啟搜尋方塊右邊的下拉式清單。

2. 選擇新的準則。

3. 在引號之間輸入篩選值。

![在 [測試總管] 中篩選測試](../test/media/ute_filtertestlist.png)

> [!NOTE]
> 搜尋是區分大小寫且比對指定字串與準則值的任何部分。

|限定詞|說明|
|-|-----------------|
|**特性**|在特性分類和值中搜尋相符項目。 指定特性分類和值的語法是由單元測試架構所定義。|
|**Project**|在測試專案名稱中搜尋相符項目。|
|**錯誤訊息**|在失敗的判斷提示所傳回之使用者定義錯誤訊息中搜尋相符項目。|
|**檔案路徑**|在測試來源檔的完整檔案名稱中搜尋相符項目。|
|**完整名稱**|在測試命名空間、類別和方法的完整檔案名稱中搜尋相符項目。|
|**輸出**|搜尋寫入標準輸出 (stdout) 或標準錯誤 (stderr) 的使用者定義錯誤訊息。 指定輸出訊息的語法是由單元測試架構所定義。|
|**結果**|在 [測試總管] 分類名稱中搜尋相符項目：[失敗的測試]  、[略過的測試]  、[成功的測試]  。|

若要排除篩部分選條件的結果，請使用下列語法：

```cpp
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

例如，`FullName:"MyClass" - FullName:"PerfTest"` 傳回名稱包含 "MyClass" 的所有測試，但排除名稱中也包含 "PerfTest" 的測試。

## <a name="create-custom-playlists"></a>建立自訂播放清單

您可以建立和儲存想要執行或檢視為群組的測試清單。 當您選取播放清單時，即會在 [測試總管] 中顯示清單中的測試。 您可以將在測試中加入一個以上的播放清單，當您選擇預設的 [所有測試]  播放清單時，就可以使用專案中的所有測試。

![選擇播放清單](../test/media/ute_playlist.png)

**若要建立播放清單**，請在測試總管中選擇一或多項測試。 在右鍵功能表上，選擇 [新增到播放清單]   > [新增播放清單]  。 以您在 [建立新播放清單]  對話方塊中指定的名稱和位置儲存檔案。

**若要將測試加入播放清單**，請在測試總管中選擇一或多項測試。 在右鍵功能表上，選擇 [新增到播放清單]  ，然後選擇要將測試新增到其中的播放清單。

**若要開啟播放清單**，請選擇 Visual Studio 功能表上的 [測試]   > [播放清單]  ，然後從最近使用過的播放清單的清單中選擇，或選擇 [開啟播放清單]  指定播放清單的名稱和位置。

如果個別測試沒有任何會防止它們依任意順序執行的相依性，請使用工具列上的 ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) 切換按鈕開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。

## <a name="debug-and-analyze-unit-tests"></a>偵錯和分析單元測試

您可以使用 [測試總管] 來啟動測試的偵錯工作階段。 使用 Visual Studio 偵錯工具逐步執行程式碼可讓您順暢地在單元測試和受測專案之間來回進行。 啟動偵錯：

1. 在 Visual Studio 編輯器中，於您要偵錯的一個或多個測試方法中設定中斷點。

    > [!NOTE]
    > 由於測試方法可以依照任何順序執行，請在您要偵錯的所有測試方法中設定中斷點。

2. 在 [測試總管] 中，選取測試方法，然後選擇右鍵功能表上的 [偵錯選取的測試]  。

   如需偵錯工具的詳細資訊，請參閱[在 Visual Studio 中偵錯](../debugger/debugger-feature-tour.md)。

### <a name="diagnose-test-method-performance-issues"></a>診斷測試方法效能問題

若要診斷測試方法為何花費太多時間，請在 [測試總管] 中選取該方法，然後選擇右鍵功能表上的 [設定檔]  。 請參閱[效能總管](../profiling/performance-explorer.md)。

### <a name="analyze-unit-test-code-coverage"></a>分析單元測試程式碼涵蓋範圍

您可以使用 Visual Studio 程式碼涵蓋範圍工具來判斷您的單元測試實際測試的產品程式碼數量。 您可以在方案中的所選測試或所有測試上執行程式碼涵蓋範圍。

若要在方案中執行測試方法的程式碼涵蓋範圍：

1. 選擇頂端功能表列上的 [測試]  ，然後選擇 [分析程式碼涵蓋範圍]  。

2. 從子功能表選擇下列其中一個命令：

    - [選取的測試]  會執行您在 [測試總管] 中所選取的測試方法。

    - [所有測試]  會執行方案中的所有測試方法。

[程式碼涵蓋範圍結果]  視窗會顯示線條、函式、類別、命名空間及模組所運用的產品程式碼區塊的百分比。

如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

## <a name="test-shortcuts"></a>測試快速鍵

測試可以從 [測試總管]  執行，方法是在程式碼編輯器中，以滑鼠右鍵按一下測試，並選取 [執行測試]  ，或是在 Visual Studio 中使用預設的 [[測試總管] 快速鍵](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)。 部分快速鍵是以內容為基礎。 這表示它們會根據您的游標在程式碼編輯器中的位置來執行或偵錯測試。 如果游標在測試方法內，則該測試方法便會執行。 如果游標是在類別層級，則該類別中的所有測試便會執行。 對於命名空間層級也是如此。

|常見命令| 鍵盤快速鍵|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl**+**R**、**Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**Ctrl**+**R**、**T**|

> [!NOTE]
> 您不能在抽象類別中執行測試，因為測試只定義於抽象類別，而不會具現化。 若要在抽象類別執行測試，請建立衍生自抽象類別的類別。

## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [以 64 位元處理序的形式執行單元測試](../test/run-a-unit-test-as-a-64-bit-process.md)
- [測試清單編輯器常見問題集](test-explorer-faq.md)
