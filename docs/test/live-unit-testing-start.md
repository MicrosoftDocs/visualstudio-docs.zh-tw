---
title: 了解如何使用 Live Unit Test 來測試程式碼
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5b136c91873c0af60705ea361a19e53f28e06b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653048"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing 的使用者入門

當您在 Visual Studio 方案中啟用 Live Unit Testing 時，它會以視覺化方式描述測試涵蓋範圍和測試的狀態。 Live Unit Testing 也會在您修改程式碼時動態執行測試，並在變更導致測試失敗時立即通知您。

Live Unit Testing 可以用來測試以 .NET Framework 或 .NET Core 為目標的解決方案。 在本教學課程中，您將瞭解如何藉由建立以 .NET Standard 為目標的簡單類別庫來使用 Live Unit Testing，而且您會建立以 .NET Core 為目標的 MSTest 專案來進行測試。

您可以從 GitHub 的 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) 存放庫下載完整 C# 方案。

## <a name="prerequisites"></a>Prerequisites

本教學課程需要您已安裝具有 **.Net Core 跨平臺開發**工作負載的 Visual Studio Enterprise edition。

## <a name="create-the-solution-and-the-class-library-project"></a>建立方案和類別庫專案

一開始先建立名為 UtilityLibraries 的 Visual Studio 方案，其中包含單一 .NET Standard 類別庫專案 StringLibrary。

方案只是一或多個專案的容器。 若要建立空白方案，請開啟 Visual Studio 並執行下列作業：

1. 從頂層 Visual Studio 功能表中，依序選取 [檔案] > 、[新增] > [專案]。

1. 在範本搜尋方塊中鍵入 [方案]，然後選取 [空白方案] 範本。

   ::: moniker range="vs-2017"

   ![[新增專案] 對話方塊](./media/lut-start/new-solution.png)

   ::: moniker-end

1. 完成建立方案。

既然您已建立方案，您將會建立名為 StringLibrary 的類別庫，其中包含一些用於處理字串的擴充方法。

1. 在**方案總管**中，以滑鼠右鍵按一下 UtilityLibraries 方案，然後選取 [**加入** > **新增專案**]。

::: moniker range="vs-2017"

2. 在 [新增專案] 對話方塊中，選取 C# 節點，然後選取 [.NET Standard]。

   > [!NOTE]
   > 因為我們的程式庫是以 .NET Standard 而不是特定的 .NET 實作為目標，所以可以從任何支援該版本 .NET Standard 的 .NET 實作為呼叫。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

3. 在右窗格中選取 [**類別庫（.NET Standard）** ] 範本，然後在 [**名稱**] 文字方塊中輸入**StringLibrary** ，如下圖所示：

   ![[新增專案] 對話方塊](./media/lut-start/add-project-cs.png)

4. 選取 [確定] 建立專案。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在範本的搜尋方塊中鍵入**類別庫**，然後選取 [類別庫 (.NET Standard)] 範本。 按 [ **下一步**]。

   > [!NOTE]
   > 因為我們的程式庫是以 .NET Standard 而不是特定的 .NET 實作為目標，所以可以從任何支援該版本 .NET Standard 的 .NET 實作為呼叫。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

3. 將專案命名為**StringLibrary**。

4. 按一下 [建立] 以建立專案。

::: moniker-end

5. 將程式碼視窗中的所有現有程式碼都取代為下列程式碼：

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary 有三個靜態方法：

   - 如果字串的開頭是大寫字元，則 `StartsWithUpper` 會傳回 `true`；否則會傳回 `false`。

   - 如果字串的開頭是小寫字元，則 `StartsWithLower` 會傳回 `true`；否則會傳回 `false`。

   - 如果字串包含內嵌空白字元，則 `HasEmbeddedSpaces` 會傳回 `true`；否則會傳回 `false`。

6. 從最上層 Visual Studio 功能表中，依序選取 [建置] > [建置方案]。 組建應會成功。

## <a name="create-the-test-project"></a>建立測試專案

下一個步驟是建立單元測試專案來測試 StringLibrary 程式庫。 執行下列步驟，以建立單元測試：

1. 在**方案總管**中，以滑鼠右鍵按一下 UtilityLibraries 方案，然後選取 [**加入** > **新增專案**]。

::: moniker range="vs-2017"

2. 在 [新增專案] 對話方塊中，選取 C# 節點，然後選取 [.NET Core]。

   > [!NOTE]
   > 您不需要使用與類別庫相同的語言來撰寫單元測試。

3. 在右窗格中選取 [**單元測試專案（.Net Core）** ] 範本，然後在 [**名稱**] 文字方塊中輸入**StringLibraryTests** ，如下圖所示：

   ![單元測試專案的 [新增專案] 對話方塊](./media/lut-start/add-unit-test-cs.png)

4. 選取 [確定] 建立專案。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在範本搜尋方塊中鍵入**單元測試**，然後選取 [單元測試專案 (.NET Core)] 範本。 按 [ **下一步**]。

3. 將專案命名為**StringLibraryTests**。

4. 按一下 [建立] 以建立專案。

::: moniker-end

   > [!NOTE]
   > 本入門教學課程會搭配使用 Live Unit Testing 與 MSTest 測試架構。 您也可以使用 xUnit 和 NUnit 測試架構。

5. 單元測試專案無法自動存取所測試的類別程式庫。 您可以新增類別庫專案的參考，以提供測試程式庫存取權。 若要執行這個作業，請以滑鼠右鍵按一下 `StringLibraryTests` 專案，然後依序選取 [新增] > [參考]。 在 [**參考管理員**] 對話方塊中，確認已選取 [**方案**] 索引標籤，然後選取 [StringLibrary] 專案，如下圖所示。

   ![[參考管理員] 對話方塊](./media/lut-start/add-reference.png)

6. 將範本所提供的未定案單元測試程式碼取代為下列程式碼：

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. 選取工具列上的**儲存**圖示，以儲存專案。

8. 由於單元測試程式碼包含一些非 ASCII 字元，因此 Visual Studio 會顯示下列對話方塊，以警告當您將檔案儲存為預設 ASCII 格式時，將會遺失某些字元。 選擇 [用其他編碼儲存] 按鈕。

   ![選擇檔案編碼](media/lut-start/ascii-encoding.png)

9. 在 [**預付款儲存選項**] 對話方塊的 [**編碼**] 下拉式清單中，選擇 [ **Unicode （utf-8 無簽章）-字碼頁 65001**]，如下圖所示：

   ![選擇 UTF-8 編碼](media/lut-start/utf8-encoding.png)

10. 從最上層的 Visual Studio 功能表，選取 [建置]  >  [重建方案]，以編譯單元測試專案。

您已為其建立類別庫以及一些單元測試。 您現在已完成使用 Live Unit Testing 所需的準備工作。

## <a name="enable-live-unit-testing"></a>啟用 Live Unit Testing

到目前為止，雖然您已撰寫 StringLibrary 類別庫的測試，但尚未執行。 Live Unit Testing 會在啟用之後自動執行它們。 若要這麼做，請執行下列作業：

1. （選擇性）選取包含 StringLibrary 程式碼的程式碼視窗。 這是 *Class1.cs* (適用於 C# 專案) 或 *Class1.vb* (適用於 Visual Basic 專案) （此步驟可讓您在啟用 Live Unit Testing 之後，以視覺化方式檢查測試結果和程式碼涵蓋範圍的範圍）。

1. 從最上層 Visual Studio 功能表中，依序選取 [測試] > [Live Unit Testing] > [啟動]。

1. Visual Studio 會啟動 Live Unit Test，以自動執行所有測試。

完成執行測試之後，**測試總管**會顯示整體結果和個別測試結果。 此外，程式碼視窗會以圖形方式顯示測試程式碼涵蓋範圍和測試結果。 如下圖所示，這三項測試都已順利執行。 它也會顯示我們的測試已涵蓋 `StartsWithUpper` 方法中的所有程式碼路徑，而且已成功執行這些測試 (以綠色核取記號 "✓" 指出)。 最後，它會顯示 StringLibrary 中的其他方法都沒有程式碼涵蓋範圍（以藍色線表示的「➖」）。

![啟動 Live Unit Testing 之後的測試總管和程式碼視窗](media/lut-start/lut-results-cs.png)

您也可以選取程式碼視窗中的特定程式碼涵蓋範圍圖示，來取得測試涵蓋範圍和測試結果的更詳細資訊。 若要檢查此詳細資料，請執行下列作業：

1. 按一下 `StartsWithUpper` 方法之 `if (String.IsNullOrWhiteSpace(s))` 行中的綠色核取記號。 如下圖所示，Live Unit Testing 指出三個測試涵蓋該程式程式碼，而且全部都已順利執行。

   !['if' 條件陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs1.png)

1. 按一下 `StartsWithUpper` 方法之 `return Char.IsUpper(s[0])` 行中的綠色核取記號。 如下圖所示，Live Unit Testing 表示只有兩個測試涵蓋該程式程式碼，而且全部都已順利執行。

   ![return 陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs2.png)

Live Unit Testing 所識別的主要問題是不完整的程式碼涵蓋範圍。 您將在下節中解決它。

## <a name="expand-test-coverage"></a>展開測試涵蓋範圍

在本節中，您會將單元測試擴充至 `StartsWithLower` 方法。 當您這麼做時，Live Unit Testing 會動態繼續測試您的程式碼。

若要將程式碼涵蓋範圍擴充至 `StartsWithLower` 方法，請執行下列作業：

1. 將下列 `TestStartsWithLower` 和 `TestDoesNotStartWithLower` 方法新增至專案的測試原始程式檔：

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. 在 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) 方法呼叫之後立即新增下列程式碼，來修改 `DirectCallWithNullOrEmpty` 方法。

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing 會在您修改原始程式碼時自動執行新的和修改過的測試。 如同 [ **Test Explorer** ] 的下圖所示，所有測試（包括您所加入的兩個）和您已修改的測試都已成功。

   ![展開測試涵蓋範圍之後的測試瀏覽器](media/lut-start/test-dynamic.png)

1. 切換至包含 StringLibrary 類別之原始程式碼的視窗。 Live Unit Testing 現在會顯示我們的程式碼涵蓋範圍擴充至 `StartsWithLower` 方法。

    ![StartsWithLower 方法的程式碼涵蓋範圍](media/lut-start/lut-extended-cs.png)

在某些情況下，**測試瀏覽器**中成功的測試可能會呈現灰色。這表示目前正在執行測試，或測試未再次執行，因為自從上次執行後，沒有任何程式碼變更會影響測試。

截至目前為止，所有測試均為成功。 在下節中，我們將檢查如何處理測試失敗。

## <a name="handle-a-test-failure"></a>處理測試失敗

在本節中，您將探索如何使用 Live Unit Testing 來識別、疑難排解和解決測試失敗。 做法是將測試涵蓋範圍展開至 `HasEmbeddedSpaces` 方法。

1. 將下列方法新增至測試檔案：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. 當測試執行時，Live Unit Testing 表示 `TestHasEmbeddedSpaces` 方法失敗，如下圖所示：

   ![測試 Explorer 報告失敗的測試](media/lut-start/test-failure.png)

1. 選取顯示程式庫程式碼的視窗。 Live Unit Testing 已擴充 `HasEmbeddedSpaces` 方法的程式碼涵蓋範圍。 它也會在失敗測試所涵蓋的程式行中新增紅色 "🞩"，以報告測試失敗。

1. 將游標停留在含 `HasEmbeddedSpaces` 方法簽章的行上方。 Live Unit Testing 會顯示工具提示，報告該方法已由一個測試涵蓋，如下圖所示：

   ![失敗測試的 Live Unit Testing 資訊](media/lut-start/test-failure-info-cs.png)

1. 選取失敗的 **TestHasEmbeddedSpaces** 測試。 Live Unit Testing 提供了數個選項，例如執行所有測試、執行選取的測試、對所有測試進行調試，以及對選取的測試進行調試，如下圖所示：

   ![失敗測試的 Live Unit Testing 選項](media/lut-start/test-failure-options.png)

1. 選取 [偵錯選取的測試]，以偵錯失敗的測試。

1. Visual Studio 會以偵錯模式執行測試。

   測試會將陣列中的每個字串指派給名為 `phrase` 的變數，並將它傳遞給 `HasEmbeddedSpaces` 方法。 assert 運算式第一次為 `false` 時，執行程式會暫停並叫用偵錯工具。 下圖顯示來自[`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue)方法呼叫中非預期值所產生的例外狀況對話方塊。

   ![Live Unit Testing 例外狀況對話方塊](media/lut-start/exception-dialog-cs.png)

   此外，Visual Studio 提供的所有偵錯工具都可協助我們疑難排解失敗的測試，如下圖所示：

   ![Visual Studio 調試工具](media/lut-start/debugging-tools-cs.png)

   請注意，在 `phrase` 變數值為 "Name\tDescription" (即陣列的第二個項目) 的 [自動變數] 視窗中。 測試方法預期 `HasEmbeddedSpaces` 在收到此字串時傳回 `true`；但卻傳回 `false`。 顯然，它無法將 "\t" (定位字元) 辨識為內嵌空格。

1. 選取 [偵錯] > [繼續]、按 **F5**，或按一下工具列上的 [繼續] 按鈕，繼續執行測試程式。 因為發生無法處理的例外狀況，所以測試終止。
這提供初步調查 Bug 的足夠資訊。 `TestHasEmbeddedSpaces` (測試常式) 的假設錯誤，或 `HasEmbeddedSpaces` 未正確地辨識所有內嵌空格。

1. 若要診斷並更正問題，請從 `StringLibrary.HasEmbeddedSpaces` 方法開始。 查看 `HasEmbeddedSpaces` 方法中的比較。 它會將內嵌空格視為 U+0020。 不過，Unicode Standard 包含許多其他空格字元。 這可能表示不正確地測試程式庫程式碼的空格字元。

1. 將相等比較取代為 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 方法呼叫：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing 會自動重新執行失敗的測試方法，並更新程式碼視窗和**測試瀏覽器**中的結果，如下圖所示：

    ![成功的 HasEmbeddedSpaces 測試](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>請參閱

- [Visual Studio 中的 Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing 常見問題集](live-unit-testing-faq.md)