---
title: 使用測試總管執行單元測試
description: 了解如何在 Visual Studio 中使用 [測試總管] 執行測試。 本主題說明如何在組建、查看測試結果、群組和篩選測試清單、建立播放清單，以及使用測試快速鍵的情況下，啟用自動測試回合。
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 26dbed25f42f40614597075ad26c855398b56025
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925120"
---
# <a name="run-unit-tests-with-test-explorer"></a>使用測試總管執行單元測試

使用 [測試總管] 從 Visual Studio 或協力廠商單元測試專案中執行單元測試。 您也可以使用 [測試總管] 將測試分組成分類、篩選測試清單，以及建立、儲存和執行測試播放清單。 您也可以分析程式碼涵蓋範圍和 [偵錯工具單元測試](../test/debug-unit-tests-with-test-explorer.md)。

**Test Explorer** 可以從方案中的多個測試專案，以及屬於實際執行程式碼專案的測試類別來執行測試。 測試專案可以使用不同的單元測試架構。 當進行測試的程式碼是為 .NET 撰寫時，測試專案可以用任何同樣以 .NET 為目標的語言撰寫，而不管目標程式碼的語言為何。 原生 C/C++ 程式碼專案必須使用 C++ 單元測試架構進行測試。

## <a name="build-your-test-project"></a>建立您的測試專案

如果您的 Visual Studio 方案中尚未設定測試專案，您必須先建立並建立測試專案。

- [ ( .NET) 開始使用單元測試 ](../test/getting-started-with-unit-testing.md)
- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)

Visual Studio 2015 包含 Managed 程式碼和機器碼皆適用的 Microsoft 單元測試架構。 不過，測試總管也可以執行任何已實作測試總管配接器的單元測試架構。 如需安裝協力廠商單元測試架構的詳細資訊，請參閱[安裝協力廠商單元測試架構](../test/install-third-party-unit-test-frameworks.md)。

## <a name="run-tests-in-test-explorer"></a>在 [測試總管] 中執行測試

在建置測試專案後，這些測試便會出現在 [測試總管] 中。 如果看不到 Test Explorer，請選擇 [Visual Studio] 功能表上的 [**測試**]，選擇 [**視窗**]，然後選擇 [ **test Explorer** ] (或按 **Ctrl**  +  **E**， **T**) 。

::: moniker range="vs-2017"
![單元測試總管](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![測試總管](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
當您執行、寫入、重新執行您的測試時，測試總管會顯示 [失敗的測試] 、[通過的測試] 、[略過的測試]  和 [未執行的測試] 預設群組中的結果。 您可以變更測試總管群組測試的方式。
::: moniker-end
::: moniker range=">=vs-2019"
當您執行、撰寫及重新執行測試時，[測試總管] 會將結果顯示在預設的 [專案]、[命名空間] 及 [類別] 群組中。 您可以變更 [測試總管] 將測試分組的方式。
::: moniker-end

您可以從 [測試總管] 工具列，執行尋找、組織及執行測試等許多工作。

::: moniker range="vs-2017"
![從 [測試總管] 的工具列執行測試](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![從 [測試總管] 的工具列執行測試](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>執行測試

::: moniker range="vs-2017"
您可以執行方案中的所有測試、群組中的所有測試，或是您選取的一組測試。 執行下列其中一個動作：

- 若要執行方案中的所有測試，請選擇 [ **執行所有** (]，或按 **Ctrl** + **R**、 **V**) 。

- 若要執行預設群組中的所有測試，請選擇 [ **執行** ]，然後選擇功能表上的群組。

- 選取您要執行的個別測試，開啟所選測試的右鍵功能表，然後選擇 [ **執行選取的測試** ] (或按下 **Ctrl** + **R**、 **T**) 。

- 如果個別測試沒有任何會防止它們依任意順序執行的相依性，請使用工具列上的 ![Visual Studio Test Explorer 工具列上 [平行測試執行] 切換按鈕的螢幕擷取畫面。 選取此按鈕時，將會以平行方式執行測試。](../test/media/ute_parallelicon-small.png) 切換按鈕開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。

執行測試時，[測試總管] 視窗頂端會動畫呈現 **成功/失敗列**。 測試回合結束時，如果所有測試皆成功，**成功/失敗列** 會變成綠色；如果有任何一個測試失敗，則會變成紅色。
::: moniker-end
::: moniker range=">=vs-2019"
您可以執行方案中的所有測試、群組中的所有測試，或是您選取的一組測試。 執行下列其中一個動作：

- 若要執行方案中的所有測試，請選擇 [ **全部執行** ] 圖示 (或按 **Ctrl** + **R**、 **V**) 。

- 若要執行預設群組中的所有測試，請選擇 [執行] 圖示，然後在功能表上選擇該群組。

- 選取您要執行的個別測試，開啟所選測試的右鍵功能表，然後選擇 [ **執行選取的測試** ] (或按下 **Ctrl** + **R**、 **T**) 。

- 如果個別測試沒有任何會防止它們依任意順序執行的相依性，請使用工具列的設定功能表開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。
::: moniker-end

### <a name="run-tests-after-every-build"></a>每次建置後執行測試
::: moniker range="vs-2017"
|按鈕|描述|
|-|-|
|![建置後執行](../test/media/ute_runafterbuild_btn.png)|若要在每次本機建置之後執行單元測試，請在標準功能表中選擇 [測試]，然後選擇 [測試總管] 工具列上的 [建置之後執行測試]。|

> [!NOTE]
> 若要在每次建置後執行單元測試，必須具備 Visual Studio 2017 Enterprise 或 Visual Studio 2019。 Visual Studio 2019 的 Community、Professional 和 Enterprise 版均隨附此功能。
::: moniker-end
::: moniker range=">=vs-2019"
若要在每次進行本機建置之後執行單元測試，請開啟 [測試總管] 中的設定圖示，然後選取 [建置之後執行測試]。
::: moniker-end

## <a name="view-test-results"></a>檢視測試結果

當您執行、寫入、重新執行您的測試時，測試總管會顯示 [失敗的測試] 、[通過的測試] 、[略過的測試]  和 [未執行的測試] 群組中的結果。 在 [測試總管] 底部或一側的詳細資料窗格會顯示測試回合的摘要。

### <a name="view-test-details"></a>檢視測試詳細資料

若要檢視個別測試的詳細資料，請選取該測試。

::: moniker range="vs-2017"
![測試執行詳細資料](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![測試執行詳細資料](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

測試詳細資料窗格會顯示下列資訊：

- 測試方法的原始檔案名稱和行號。

- 測試的狀態。

- 測試方法執行的經過時間。

如果測試失敗，詳細資料窗格也會顯示：

- 測試的單元測試架構所傳回的訊息。

- 測試失敗時的堆疊追蹤。

### <a name="view-the-source-code-of-a-test-method"></a>檢視測試方法的原始程式碼

若要在 Visual Studio 編輯器中顯示測試方法的原始程式碼，請選取測試，然後選擇右鍵功能表上的 [ **開啟測試** ] (或按 **F12**) 。

## <a name="group-and-filter-the-test-list"></a>群組和篩選測試清單

測試總管可讓您將測試分組到預先定義的分類。 在測試總管中執行的大部分單元測試架構可讓您定義自己的分類和分類/值組來群組您的測試。 您也可以透過比對字串和測試屬性來篩選測試清單。

### <a name="group-tests-in-the-test-list"></a>將測試清單中的測試分組

::: moniker range="vs-2017"
若要變更測試的組織方式，請選擇 [群組依據] 按鈕 ![測試總管的 [群組] 按鈕](../test/media/ute_groupby_btn.png)旁邊的向下箭號，然後選取新的分組準則。

![在 [測試總管] 中依分類為測試分組](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
[測試總管] 可讓您將測試分組至某個階層。 預設的階層群組是 [專案]、[命名空間]，然後是 [類別]。 若要變更測試的組織方式，請選擇 [分組依據] 按鈕 ![[測試總管] 的 [群組] 按鈕](../test/media/ute_groupby_btn.png)，然後選取新的分組準則。

![在 [測試總管] 中依分類為測試分組](../test/media/vs-2019/test-explorer-groupby-162.png)

您可以定義自己的階層層級，然後依您偏好的順序選取 [分組依據] 選項，例如先依 [狀態] 再依 [類別] 進行分組。

![[Visual Studio Test Explorer] 的螢幕擷取畫面，其中顯示一個窗格中的測試階層，以及另一個窗格中的 [群組依據] 功能表，並選取 [類別] 和 [狀態] 選項。](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>測試總管群組

::: moniker range="vs-2017"
|群組|描述|
|-|-----------------|
|**有效期間**|依據執行時間群組測試：[快] 、[中] 和 [慢] 。|
|**結果**|依據執行結果群組測試：[失敗的測試] 、[略過的測試] 、[成功的測試] 。|
|**特性**|依據您定義的分類/值組群組測試。 指定特性分類和值的語法是由單元測試架構所定義。|
|**專案**|依據名稱專案群組測試。|
::: moniker-end
::: moniker range=">=vs-2019"
|群組|描述|
|-|-----------------|
|**有效期間**|依執行時間將測試分組： **Fast**、 **Medium** 和 **慢**。|
|**State**|依執行結果將測試分組： **失敗的測試**、 **略過的測試**、已通過的 **測試**、 **未執行**|
|**目標 Framework** | 依其專案的目標架構將測試分組 |
|**Namespace**|依上層命名空間將測試分組。|
|**專案**|依上層專案將測試分組。|
|**類別**|依上層類別將測試分組。|
::: moniker-end

### <a name="traits"></a>特性

特性通常是分類名稱/值組，但也可以是單一分類。 您可將特性指派給方法，其中單元測試架構可將其識別為測試方法。 單元測試架構可以定義特性分類。 您可以將值加入特性分類以定義自己的分類名稱/值組。 指定特性分類和值的語法是由單元測試架構所定義。

**Microsoft Managed 程式碼單元測試架構中的特性**

Microsoft Managed 程式碼單元測試架構中，您可在  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> 屬性中定義特性名稱/值組。 測試架構也包含下列預先定義的特性：

|特徵|描述|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|擁有者分類是由單元測試架構所定義，會要求您提供擁有者的字串值。|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|優先權分類是由單元測試架構所定義，會要求您提供優先權的整數值。|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|TestCategory 屬性可讓您指定單元測試的類別。|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|TestProperty 屬性可讓您定義特性分類/值組。|


**Microsoft C++ 單元測試架構中的特性**

請參閱[如何使用適用於 C++ 的 Microsoft 單元測試架構](how-to-use-microsoft-test-framework-for-cpp.md)。

## <a name="create-custom-playlists"></a>建立自訂播放清單

::: moniker range="vs-2017"
您可以建立和儲存想要執行或檢視為群組的測試清單。 當您選取播放清單時，即會在 [測試總管] 中顯示清單中的測試。 您可以將在測試中加入一個以上的播放清單，當您選擇預設的 [所有測試]  播放清單時，就可以使用專案中的所有測試。

![選擇播放清單](../test/media/ute_playlist.png)

**若要建立播放清單**，請在測試總管中選擇一或多項測試。 在右鍵功能表上，選擇 [**加入至播放清單**]  >  **[]**。 以您在 [建立新播放清單]  對話方塊中指定的名稱和位置儲存檔案。

**若要將測試加入播放清單**，請在測試總管中選擇一或多項測試。 在右鍵功能表上，選擇 [新增到播放清單]，然後選擇要將測試新增到其中的播放清單。

**若要開啟播放清單**，請從 [Visual Studio] 功能表選擇 [ **測試** > **播放清單** ]，然後從最近使用的播放清單中選擇，或選擇 [ **開啟播放清單** ] 指定播放清單的名稱和位置。

如果個別測試沒有任何會防止它們依任意順序執行的相依性，請使用工具列上的 ![Visual Studio Test Explorer 工具列上 [平行測試執行] 切換按鈕的螢幕擷取畫面。](../test/media/ute_parallelicon-small.png) 切換按鈕開啟平行測試執行。 這可大幅縮短執行所有測試所需的時間。
::: moniker-end
::: moniker range=">=vs-2019"
您可以建立和儲存想要執行或檢視為群組的測試清單。 當您選取播放清單時，清單中的測試會顯示在新的 [測試瀏覽器] 索引標籤中。您可以將測試新增至多個播放清單。

**若要建立播放清單**，請在測試總管中選擇一或多項測試。 在右鍵功能表上，選擇 [新增 **到播放清單**]  >  **新播放清單**。

![建立播放清單](../test/media/vs-2019/test-explorer-playlist-16-2.png)

播放清單會在新的 [測試瀏覽器] 索引標籤中開啟。您可以使用此播放清單一次，然後捨棄它，也可以按一下播放清單視窗工具列中的 [ **儲存** ] 按鈕，然後選取要儲存播放清單的名稱和位置。

![播放清單會在個別的測試總管索引標籤中開啟](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**若要建立播放清單**，請在測試總管中選擇一或多項測試。 按一下滑鼠右鍵，然後選擇 [新增 **到播放清單**]  >  **新播放清單**。

**若要開啟播放清單**，選擇 Visual Studio 工具列中的播放清單圖是，然後從功能表中選取先前儲存的播放清單檔案。

**若要編輯播放清單**，您可以用滑鼠右鍵按一下任何測試，然後使用功能表選項，從播放清單中新增或移除播放清單。

從 Visual Studio 2019 版本16.7 開始，您可以選擇工具列中的 [ **編輯** ] 按鈕。 測試旁邊會出現核取方塊，顯示播放清單中包含和排除的測試。 視需要編輯群組。

![編輯播放清單按鈕](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

您也可以選取或取消選取階層中父群組的方塊。 此動作會建立動態播放清單，一律會根據該群組中的測試來更新播放清單。 例如，如果您在類別旁放置核取記號，從該類別新增的任何測試都會變成此播放清單的一部分。 如果您從該類別刪除測試，它就會從播放清單中移除。 您可以使用工具列中的 [儲存] 按鈕來儲存播放清單，並開啟在您的磁片上建立的 *播放清單* 檔案，以深入瞭解規則。 此檔案會列出組成播放清單的所有規則和個別測試。

![播放清單 xml 檔案](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

如果您想要建立特性的播放清單，請使用下列適用于 MSTest 的格式。
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

針對 xUnit，請使用下列格式。 請確定您的名稱與之間有一個空格 `TestCategory` `[Value]` 。
```xml
<Playlist Version="2.0">
  <Rule Name="Includes" Match="Any">
    <Rule Match="All">
      <Property Name="Solution" />
        <Rule Match="Any">
            <Property Name="Trait" Value="TestCategory [Value]" />
        </Rule>
    </Rule>
  </Rule>
</Playlist>
```

::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>測試總管資料行

[群組](#test-explorer-groups) 在 [測試總管] 中也與 [特性]、[堆疊追蹤]、[錯誤訊息] 及 [完整名稱] 一起可供作為資料行。 大多數資料行預設並不可見，而您可以自訂要看見的資料行及其顯示順序。

![[Visual Studio Test Explorer] 的螢幕擷取畫面，其中顯示已選取資料行的功能表，以及已選取 [持續時間]、[特性] 和 [錯誤訊息] 的子功能表。](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>篩選、排序及重新排列測試資料行

您可以篩選、排序及重新排列資料行。
* 若要篩選成特定特性，請按一下 [特性] 資料行頂端的篩選圖示。

  ![資料行篩選](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* 若要變更資料行的順序，請按一下資料行標頭，然後將其向左或右拖曳。

* 若要排序資料行，請按一下資料行標頭。 並非所有資料行都可以進行排序。 您也可以按住 **Shift** 鍵，然後按一下其他的資料行標頭，依次要資料行進行排序。

  ![資料行排序](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>搜尋和篩選測試清單

您也可以使用 [測試總管] 搜尋篩選，以限制您檢視和執行之專案中的測試方法。

當您在 [測試總管] 的搜尋方塊鍵入字串並選擇 **Enter** 時，會將測試清單篩選為只顯示包含該字串之完整名稱的測試。

若要依據不同準則篩選：

1. 開啟搜尋方塊右邊的下拉式清單。

2. 選擇新的準則。

3. 在引號之間輸入篩選值。 如果您想要搜尋完全相符的字串，而不是包含的相符項目，請使用等號 (=)，而不是冒號 (:)。

::: moniker range="vs-2017"
![在 [測試總管] 中篩選測試](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![在 [測試總管] 中篩選測試](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> 搜尋是區分大小寫且比對指定字串與準則值的任何部分。

::: moniker range="vs-2017"
|Qualifier|描述|
|-|-----------------|
|**特徵**|在特性分類和值中搜尋相符項目。 指定特性分類和值的語法是由單元測試架構所定義。|
|**專案**|在測試專案名稱中搜尋相符項目。|
|**錯誤訊息**|在失敗的判斷提示所傳回之使用者定義錯誤訊息中搜尋相符項目。|
|**檔案路徑**|在測試來源檔的完整檔案名稱中搜尋相符項目。|
|**完整名稱**|在測試命名空間、類別和方法的完整名稱中搜尋相符項目。|
|**輸出**|搜尋寫入標準輸出 (stdout) 或標準錯誤 (stderr) 的使用者定義錯誤訊息。 指定輸出訊息的語法是由單元測試架構所定義。|
|**結果**|在測試總管分類名稱中搜尋相符項目：[失敗的測試] 、[略過的測試] 、[成功的測試] 。|
::: moniker-end
::: moniker range=">=vs-2019"
|Qualifier|描述|
|-|-----------------|
|**State**|在測試總管分類名稱中搜尋相符項目：[失敗的測試] 、[略過的測試] 、[成功的測試] 。|
|**特性**|在特性分類和值中搜尋相符項目。 指定特性分類和值的語法是由單元測試架構所定義。|
|**完整名稱**|在測試命名空間、類別和方法的完整名稱中搜尋相符項目。|
|**專案**|在測試專案名稱中搜尋相符項目。|
|**目標 Framework**|在測試總管分類名稱中搜尋相符項目：[失敗的測試] 、[略過的測試] 、[成功的測試] 。|
|**Namespace**|在測試命名空間中搜尋相符項目。|
|**類別**|在測試類別名稱中搜尋相符項目。|
::: moniker-end

若要排除篩部分選條件的結果，請使用下列語法：

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

例如，`FullName:"MyClass" - FullName:"PerfTest"` 傳回名稱包含 "MyClass" 的所有測試，但排除名稱中也包含 "PerfTest" 的測試。

### <a name="analyze-unit-test-code-coverage"></a>分析單元測試程式碼涵蓋範圍

您可以使用 Visual Studio Enterprise 版中提供的 Visual Studio 程式碼涵蓋範圍工具，來判斷您的單元測試實際測試的產品程式碼數量。 您可以在方案中的所選測試或所有測試上執行程式碼涵蓋範圍。

若要在方案中執行測試方法的程式碼涵蓋範圍：

::: moniker range="vs-2017"

1. 選擇頂端功能表列上的 [測試]，然後選擇 [分析程式碼涵蓋範圍]。

2. 從子功能表選擇下列其中一個命令：

    - [選取的測試] 會執行您在 [測試總管] 中所選取的測試方法。

    - [所有測試] 會執行方案中的所有測試方法。

::: moniker-end

::: moniker range=">=vs-2019"

* 以滑鼠右鍵按一下 [Test Explorer]，然後選取 [**分析選取之測試的程式碼涵蓋範圍**]

::: moniker-end

[程式碼涵蓋範圍結果] 視窗會顯示線條、函式、類別、命名空間及模組所運用的產品程式碼區塊的百分比。

如需詳細資訊，請參閱[使用程式碼涵蓋範圍來決定所測試的程式碼數量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

## <a name="test-shortcuts"></a>測試快速鍵

您可以在測試的程式碼編輯器中按一下滑鼠右鍵，然後選取 [ **執行測試** ]，或使用 Visual Studio 中的預設 [測試瀏覽器快捷方式](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) ，從 test explorer 執行測試。 部分快速鍵是以內容為基礎。 這表示它們會根據游標在程式碼編輯器中的位置執行或偵測 [測試](../test/debug-unit-tests-with-test-explorer.md) 。 如果游標在測試方法內，則該測試方法便會執行。 如果游標是在類別層級，則該類別中的所有測試便會執行。 對於命名空間層級也是如此。

|常見命令| 鍵盤快速鍵|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl** +**R**、 **Ctrl** + **T**|
|TestExplorer.RunAllTestsInContext|**Ctrl** +**R**、 **T**|
|TestExplorer.RunAllTests|**Ctrl** +**R**、 **A**|
|TestExplorer.RepeatLastRun|**Ctrl** +**R**、 **L**|

> [!NOTE]
> 您不能在抽象類別中執行測試，因為測試只定義於抽象類別，而不會具現化。 若要在抽象類別執行測試，請建立衍生自抽象類別的類別。

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>測試音訊提示
測試執行完成時，測試瀏覽器可以播放音效。 有兩個音效：一個音效表示測試回合成功完成所有通過的測試，而第二個音效表示測試回合已完成，而且至少有一個失敗的測試。 您可以在預設的 Windows 10 音效對話方塊中設定這些音效。 這項功能從 Visual Studio 2019 Update 16.9 Preview 3 開始提供。

1. 開啟預設的 Windows 10 音效] 對話方塊。
2. 流覽 **至 [音效** ] 索引標籤。
3. 尋找 **Microsoft Visual Studio** 分類。 選擇 [ **測試回合成功** ] 或 [ **測試回合失敗** ] 音效，以選取預設音效或流覽至您自己的音訊檔案。  
![Windows 10 音效對話方塊](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>另請參閱

- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [使用測試總管進行偵錯單元測試](../test/debug-unit-tests-with-test-explorer.md)
- [以 64 位元處理序的形式執行單元測試](../test/run-a-unit-test-as-a-64-bit-process.md)
- [測試清單編輯器常見問題集](test-explorer-faq.md)
