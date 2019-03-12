---
title: 了解如何使用 Live Unit Test 來測試程式碼
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 3082f2a3acaac7b874f98d675ae28d11ea0374ae
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223766"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>在 Visual Studio 中開始使用 Live Unit Testing

在 Visual Studio 方案中啟用 Live Unit Testing 時，Live Unit Testing 會以視覺化方式說明測試涵蓋範圍和測試狀態。 這也在您修改程式碼時，動態地執行測試，並在變更導致測試失敗時隨即通知您。

Live Unit Testing 可以用來測試目標設為 .NET Framework 或 .NET Core 的方案。 在本教學課程中，您將學習如何建立目標設為 .NET Standard 的簡單類別庫來使用 Live Unit Testing，而且您將建立目標設為 .NET Core 的 MSTest 專案來進行測試。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

您可以從 GitHub 的 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) 存放庫下載完整 C# 方案。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

您可以從 GitHub 的 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) 存放庫下載完整 Visual Basic 方案。

---

## <a name="prerequisites"></a>必要條件

本教學課程需要您已安裝具有 .NET Core 2.0 工作負載的 Visual Studio Enterprise Edition。

## <a name="create-the-solution-and-the-class-library-project"></a>建立方案和類別庫專案

從建立名為 `UtilityLibraries` 的 Visual Studio 方案開始，而此方案包含單一 .NET Standard 類別庫專案 `StringLibrary`。 您可以使用 C# 或 Visual Basic 撰寫 `StringLibrary`。

方案只是一或多個專案的容器。 若要建立方案，請開啟 Visual Studio，並執行下列作業：

1. 從頂層 Visual Studio 功能表中，依序選取 [檔案] > 、[新增] > [專案]。

1. 在 [新增專案] 對話方塊中，展開 [其他專案類型] 節點，然後選取 [Visual Studio 方案]。 選取右窗格中的 [空白方案] 範本，然後在 [名稱] 文字方塊中輸入 `UtilityLibraries`，如下圖所示：

   ![[新增專案] 對話方塊](./media/lut-start/new-solution.png)

1. 選取 [確定] 建立方案。

既然您已建立方案，您將建立名為 `StringLibrary` 的類別庫，其中包含可處理字串的許多擴充方法。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 在 [方案總管] 中以滑鼠右鍵按一下 `UtilityLibraries` 方案，然後選取 [新增] > [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 C# 節點，然後選取 [.NET Standard]。

   > [!NOTE]
   > 因為我們的程式庫目標是 .NET Standard，而非特定 .NET 實作，所以可以從任何支援該版 .NET Standard 的 .NET 實作進行呼叫。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

1. 選取右窗格中的 [Class Library (.NET Standard)] (類別庫 (.NET Standard)) 範本，然後在 [名稱] 文字方塊中輸入 `StringLibrary`，如下圖所示：

   ![[新增專案] 對話方塊](./media/lut-start/add-project-cs.png)

1. 選取 [確定] 建立專案。

1. 將程式碼視窗中的所有現有程式碼都取代為下列程式碼：

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` 有三種靜態方法：

      - 如果字串的開頭是大寫字元，則 `StartsWithUpper` 會傳回 `true`；否則會傳回 `false`。

      - 如果字串的開頭是小寫字元，則 `StartsWithLower` 會傳回 `true`；否則會傳回 `false`。

      - 如果字串包含內嵌空白字元，則 `HasEmbeddedSpaces` 會傳回 `true`；否則會傳回 `false`。

1. 從最上層 Visual Studio 功能表中，依序選取 [建置] > [建置方案]。 Visual Studio 應該已成功建置程式庫。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 在 [方案總管] 中以滑鼠右鍵按一下 `UtilityLibraries` 方案，然後選取 [新增] > [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 Visual Basic 節點，然後選取 [.NET Standard]。

   > [!NOTE]
   > 因為我們的程式庫目標是 .NET Standard，而非特定 .NET 實作，所以可以從任何支援該版 .NET Standard 的 .NET 實作進行呼叫。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

1. 選取右窗格中的 [Class Library (.NET Standard)] (類別庫 (.NET Standard)) 範本，然後在 [名稱] 文字方塊中輸入 `StringLibrary`，如下圖所示：

   ![[新增專案] 對話方塊](./media/lut-start/add-project-vb.png)

1. 選取 [確定] 建立專案。

1. 將程式碼視窗中的所有現有程式碼都取代為下列程式碼：

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` 有三種靜態方法：

      - 如果字串的開頭是大寫字元，則 `StartsWithUpper` 會傳回 `true`；否則會傳回 `false`。

      - 如果字串的開頭是小寫字元，則 `StartsWithLower` 會傳回 `true`；否則會傳回 `false`。

      - 如果字串包含內嵌空白字元，則 `HasEmbeddedSpaces` 會傳回 `true`；否則會傳回 `false`。

1. 以滑鼠右鍵按一下方案總管中的 StringLibrary 專案，然後選取 [屬性]。 在 [應用程式] 索引標籤上，刪除 [根命名空間] 文字方塊中的文字，如下圖所示。 根命名空間是由原始程式碼中的 [Namespace 陳述式](/dotnet/visual-basic/language-reference/statements/namespace-statement)所定義。

   ![Visual Basic 專案的 [專案屬性] 對話方塊](./media/lut-start/vb-properties.png)

1. 從最上層 Visual Studio 功能表中，依序選取 [建置] > [建置方案]。 Visual Studio 應該已成功建置程式庫。

---

## <a name="create-the-test-project"></a>建立測試專案

下一步是建立單元測試專案，以測試 `StringLibrary` 程式庫。 執行下列步驟，以建立單元測試：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 在 [方案總管] 中以滑鼠右鍵按一下 `UtilityLibraries` 方案，然後選取 [新增] > [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 C# 節點，然後選取 [.NET Core]。

   > [!NOTE]
   > 您不需要使用與類別庫相同的語言來撰寫單元測試。

1. 選取右窗格中的 [Unit Test Project (.NET Core)] (單元測試專案 (.NET Core)) 範本，然後在 [名稱] 文字方塊中輸入 `StringLibraryTests`，如下圖所示：

   ![單元測試專案的 [新增專案] 對話方塊](./media/lut-start/add-unit-test-cs.png)

1. 選取 [確定] 建立專案。

   > [!NOTE]
   > 本入門教學課程會搭配使用 Live Unit Testing 與 MSTest 測試架構。 您也可以使用 xUnit 和 NUnit 測試架構。

1. 單元測試專案無法自動存取所測試的類別程式庫。 您可以新增類別庫專案的參考，以提供測試程式庫存取權。 若要執行這個作業，請以滑鼠右鍵按一下 `StringLibraryTests` 專案，然後依序選取 [新增] > [參考]。 在 [參考管理員] 對話方塊中，確定已選取 [方案] 索引標籤，然後選取 `StringLibrary` 專案，如下圖所示。

   ![[參考管理員] 對話方塊](./media/lut-start/add-reference.png)

1. 將範本所提供的未定案單元測試程式碼取代為下列程式碼：

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. 選取工具列上的**儲存**圖示，以儲存專案。

1. 因為單元測試程式碼包含一些非 ASCII 字元，所以 Visual Studio 會顯示下列對話方塊警告我們，如果我們將檔案儲存為其預設 ASCII 格式，則會遺失部分字元。 選擇 [用其他編碼儲存] 按鈕。

   ![選擇檔案編碼](media/lut-start/ascii-encoding.png)

1. 在 [進階儲存選項] 對話方塊的 [編碼] 下拉式清單中，選擇 [Unicode (UTF-8 沒有簽章) - 字碼頁 65001]，如下圖所示：

   ![選擇 UTF-8 編碼](media/lut-start/utf8-encoding.png)

1. 從最上層的 Visual Studio 功能表，選取 [建置]  >  [重建方案]，以編譯單元測試專案。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 在 [方案總管] 中以滑鼠右鍵按一下 `UtilityLibraries` 方案，然後選取 [新增] > [新增專案]。

1. 在 [新增專案] 對話方塊中，選取 Visual Basic 節點，然後選取 [.NET Core]。

   > [!NOTE]
   > 您不需要使用與類別庫相同的語言來撰寫單元測試。

1. 選取右窗格中的 [Unit Test Project (.NET Core)] (單元測試專案 (.NET Core)) 範本，然後在 [名稱] 文字方塊中輸入 `StringLibraryTests`，如下圖所示：

   ![單元測試的 [新增專案] 對話方塊](./media/lut-start/add-unit-test-vb.png)

1. 選取 [確定] 建立專案。

   > [!NOTE]
   > 本入門教學課程會搭配使用 Live Unit Testing 與 MSTest 測試架構。 您也可以使用 xUnit 和 NUnit 測試架構。

1. 單元測試專案無法自動存取所測試的類別程式庫。 您可以新增類別庫專案的參考，以提供測試程式庫存取權。 若要執行這個作業，請以滑鼠右鍵按一下 `StringLibraryTests` 專案，然後依序選取 [新增] > [參考]。 在 [參考管理員] 對話方塊中，確定已選取 [方案] 索引標籤，然後選取 `StringLibrary` 專案，如下圖所示。

   ![[參考管理員] 對話方塊](./media/lut-start/add-reference.png)

1. 將範本所提供的未定案單元測試程式碼取代為下列程式碼：

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. 選取工具列上的**儲存**圖示，以儲存專案。

1. 因為單元測試程式碼包含一些非 ASCII 字元，所以 Visual Studio 會顯示下列對話方塊警告我們，如果我們將檔案儲存為其預設 ASCII 格式，則會遺失部分字元。 選擇 [用其他編碼儲存] 按鈕。

   ![選擇檔案編碼](media/lut-start/ascii-encoding.png)

1. 在 [進階儲存選項] 對話方塊的 [編碼] 下拉式清單中，選擇 [Unicode (UTF-8 沒有簽章) - 字碼頁 65001]，如下圖所示：

   ![選擇 UTF-8 編碼](media/lut-start/utf8-encoding.png)

1. 透過最上層 Visual Studio 功能表中的 [建置] > [重建方案]，編譯單元測試專案。

---

您已為其建立類別庫以及一些單元測試。 您現在已完成使用 Live Unit Testing 所需的準備工作。

## <a name="enable-live-unit-testing"></a>啟用 Live Unit Testing

到目前為止，雖然您已撰寫 `StringLibrary` 類別庫的測試，但尚未執行它們。 Live Unit Testing 會在啟用之後自動執行它們。 若要這麼做，請執行下列作業：

1. 選擇性地選取包含 `StringLibrary` 程式碼的程式碼視窗。 這是 *Class1.cs* (適用於 C# 專案) 或 *Class1.vb* (適用於 Visual Basic 專案)  (此步驟可讓您在啟用 Live Unit Testing 之後，以視覺化方式檢查測試結果以及程式碼涵蓋範圍的範圍)。

1. 從最上層 Visual Studio 功能表中，依序選取 [測試] > [Live Unit Testing] > [啟動]。

1. Visual Studio 會啟動 Live Unit Test，以自動執行所有測試。

完成執行測試之後，**測試總管**會顯示整體結果和個別測試結果。 此外，程式碼視窗會以圖形方式顯示測試程式碼涵蓋範圍和測試結果。 如下圖所示，已成功執行所有這三項測試。 它也會顯示我們的測試已涵蓋 `StartsWithUpper` 方法中的所有程式碼路徑，而且已成功執行這些測試 (以綠色核取記號 "✓" 指出)。 最後，它會顯示 `StringLibrary` 中沒有其他方法具有程式碼涵蓋範圍 (以藍線 "➖" 指出)。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![啟動 Live Unit Testing 之後的測試總管和程式碼視窗](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![啟動 Live Unit Testing 之後的測試總管和程式碼視窗](media/lut-start/lut-results-vb.png)

---

您也可以選取程式碼視窗中的特定程式碼涵蓋範圍圖示，來取得測試涵蓋範圍和測試結果的更詳細資訊。 若要檢查此詳細資料，請執行下列作業：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 按一下 `StartsWithUpper` 方法之 `if (String.IsNullOrWhiteSpace(s))` 行中的綠色核取記號。 如下圖所示，Live Unit Testing 指出三項測試涵蓋該程式碼行，而且全部已成功執行。

   !['if' 條件陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs1.png)

1. 按一下 `StartsWithUpper` 方法之 `return Char.IsUpper(s[0])` 行中的綠色核取記號。 如下圖所示，Live Unit Testing 只指出兩項測試涵蓋該程式碼行，而且全部已成功執行。

   ![return 陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 按一下 `StartsWithUpper` 方法之 `If (String.IsNullOrWhiteSpace(s)) Then` 行中的綠色核取記號。 如下圖所示，Live Unit Testing 指出三項測試涵蓋該程式碼行，而且全部已成功執行。

   !['If' 條件陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-vb1.png)

1. 按一下 `StartsWithUpper` 方法之 `Return Char.IsUpper(s(0))` 行中的綠色核取記號。 如下圖所示，Live Unit Testing 只指出兩項測試涵蓋該程式碼行，而且全部已成功執行。

   ![return 陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-vb2.png)

---

Live Unit Testing 所識別的主要問題是不完整的程式碼涵蓋範圍。 您將在下節中解決它。

## <a name="expand-test-coverage"></a>展開測試涵蓋範圍

在本節中，您會將單元測試擴充至 `StartsWithLower` 方法。 當您這麼做時，Live Unit Testing 會動態繼續測試您的程式碼。

若要將程式碼涵蓋範圍擴充至 `StartsWithLower` 方法，請執行下列作業：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 將下列 `TestStartsWithLower` 和 `TestDoesNotStartWithLower` 方法新增至專案的測試原始程式檔：

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. 在 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) 方法呼叫之後立即新增下列程式碼，來修改 `DirectCallWithNullOrEmpty` 方法。

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing 會在您修改原始程式碼時自動執行新的和修改過的測試。 如**測試總管**的下圖所示，所有測試 (包含您已新增的兩項測試以及已修改的一項測試) 都已成功。

   ![展開測試涵蓋範圍之後的測試總管。](media/lut-start/test-dynamic.png)

1. 切換至包含 `StringLibrary` 類別原始程式碼的視窗。 Live Unit Testing 現在會顯示我們的程式碼涵蓋範圍擴充至 `StartsWithLower` 方法。

    ![StartsWithLower 方法的程式碼涵蓋範圍](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 將下列 `TestStartsWithLower` 和 `TestDoesNotStartWithLower` 方法新增至專案的測試原始程式檔：

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. 在 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) 方法呼叫之後立即新增下列程式碼，來修改 `DirectCallWithNullOrEmpty` 方法。

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Live Unit Testing 會在您修改原始程式碼時自動執行新的和修改過的測試。 如**測試總管**的下圖所示，所有測試 (包含您已新增的兩項測試以及已修改的一項測試) 都已成功。

   ![展開測試涵蓋範圍之後的測試總管。](media/lut-start/test-dynamic.png)

1. 切換至包含 `StringLibrary` 類別原始程式碼的視窗。 Live Unit Testing 現在會顯示我們的程式碼涵蓋範圍擴充至 `StartsWithLower` 方法。

    ![StartsWithLower 的程式碼涵蓋範圍](media/lut-start/lut-extended-vb.png)

---

在某些情況下，**測試總管**中的成功測試可能會呈現為灰色。這指出目前正在執行測試，或尚未重新執行測試，因為自上次執行之後沒有程式碼變更將影響測試。

截至目前為止，所有測試均為成功。 在下節中，我們將檢查如何處理測試失敗。

## <a name="handle-a-test-failure"></a>處理測試失敗

在本節中，您將探索如何使用 Live Unit Testing 來識別、疑難排解和解決測試失敗。 做法是將測試涵蓋範圍展開至 `HasEmbeddedSpaces` 方法。

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 將下列方法新增至測試檔案：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. 測試執行時，Live Unit Testing 指出 `TestHasEmbeddedSpaces` 方法失敗，如下圖所示：

   ![測試總管報告失敗的測試。](media/lut-start/test-failure.png)

1. 選取顯示程式庫程式碼的視窗。 請注意，Live Unit Testing 已將程式碼涵蓋範圍擴充至 `HasEmbeddedSpaces` 方法。 它也會在失敗測試所涵蓋的程式行中新增紅色 "🞩"，以報告測試失敗。

1. 將游標停留在含 `HasEmbeddedSpaces` 方法簽章的行上方。 Live Unit Testing 會顯示一個工具提示，報告某項測試涵蓋該方法，如下圖所示：

   ![失敗測試的 Live Unit Testing 資訊。](media/lut-start/test-failure-info-cs.png)

1. 選取失敗的 **TestHasEmbeddedSpaces** 測試。 請注意，Live Unit Testing 提供許多選項，例如執行所有測試、執行選取的測試、偵錯所有測試，以及偵錯選取的測試，如下圖所示：

   ![失敗測試的 Live Unit Testing 選項。](media/lut-start/test-failure-options.png)

1. 選取 [偵錯選取的測試]，以偵錯失敗的測試。

1. Visual Studio 會以偵錯模式執行測試。 我們的測試會將陣列中的每個字串都指派給名為 `phrase` 的變數，並將它傳遞給 `HasEmbeddedSpaces` 方法。 assert 運算式第一次為 `false` 時，執行程式會暫停並叫用偵錯工具。 下圖顯示 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) 方法呼叫中的未預期值所造成的例外狀況對話方塊。

   ![Live Unit Testing 例外狀況對話方塊。](media/lut-start/exception-dialog-cs.png)

   此外，Visual Studio 所提供的所有偵錯工具還可以幫助我們針對失敗的測試進行疑難排解，如下圖所示：

   ![Visual Studio 偵錯工具。](media/lut-start/debugging-tools-cs.png)

   請注意，在 `phrase` 變數值為 "Name\tDescription" (即陣列的第二個項目) 的 [自動變數] 視窗中。 測試方法預期 `HasEmbeddedSpaces` 在收到此字串時傳回 `true`；但卻傳回 `false`。 顯然，它無法將 "\t" (定位字元) 辨識為內嵌空格。

1. 選取 [偵錯] > [繼續]、按 **F5**，或按一下工具列上的 [繼續] 按鈕，繼續執行測試程式。 因為發生無法處理的例外狀況，所以測試終止。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 將下列方法新增至測試檔案：

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. 測試執行時，Live Unit Testing 指出 `TestHasEmbeddedSpaces` 方法失敗，如下圖所示：

   ![測試總管報告失敗的測試。](media/lut-start/test-failure.png)

1. 選取顯示程式庫程式碼的視窗。 請注意，Live Unit Testing 已將程式碼涵蓋範圍擴充至 `HasEmbeddedSpaces` 方法。 它也會在失敗測試所涵蓋的程式行中新增紅色 "🞩"，以報告測試失敗。

1. 將游標停留在含 `HasEmbeddedSpaces` 方法簽章的行上方。 Live Unit Testing 會顯示一個工具提示，報告某項測試涵蓋該方法，如下圖所示：

   ![失敗測試的 Live Unit Testing 資訊。](media/lut-start/test-failure-info-vb.png)

1. 選取失敗的 **TestHasEmbeddedSpaces** 測試。 請注意，Live Unit Testing 提供許多選項，例如執行所有測試、執行選取的測試、偵錯所有測試，以及偵錯選取的測試，如下圖所示：

   ![失敗測試的 Live Unit Testing 選項。](media/lut-start/test-failure-options.png)

1. 選取 [偵錯選取的測試]，以偵錯失敗的測試。

1. Visual Studio 會以偵錯模式執行測試。 我們的測試會將陣列中的每個字串都指派給名為 `phrase` 的變數，並將它傳遞給 `HasEmbeddedSpaces` 方法。 assert 運算式第一次為 `false` 時，執行程式會暫停並叫用偵錯工具。 下圖顯示 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) 方法呼叫中的未預期值所造成的例外狀況對話方塊。

   ![Live Unit Testing 例外狀況對話方塊。](media/lut-start/exception-dialog-vb.png)

   此外，Visual Studio 所提供的所有偵錯工具還可以幫助我們針對失敗的測試進行疑難排解，如下圖所示：

   ![Visual Studio 偵錯工具。](media/lut-start/debugging-tools-vb.png)

   請注意，在 `phrase` 變數值為 "Name" + vbTab + "Description" (即陣列的第二個項目) 的 [自動變數] 視窗中。 測試方法預期 `HasEmbeddedSpaces` 在收到此字串時傳回 `true`；但卻傳回 `false`。 顯然，它無法將定位字元辨識為內嵌空格。

1. 選取 [偵錯] > [繼續]、按 **F5**，或按一下工具列上的 [繼續] 按鈕，繼續執行測試程式。 因為發生無法處理的例外狀況，所以測試終止。

---

這提供初步調查 Bug 的足夠資訊。 `TestHasEmbeddedSpaces` (測試常式) 的假設錯誤，或 `HasEmbeddedSpaces` 未正確地辨識所有內嵌空格。 若要診斷和修正問題，請使用 `StringLibrary.HasEmbeddedSpaces` 方法開始：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 查看 `HasEmbeddedSpaces` 方法中的比較。 它會將內嵌空格視為 U+0020。 不過，Unicode Standard 包含許多其他空格字元。 這可能表示不正確地測試程式庫程式碼的空格字元。

1. 將相等比較取代為 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 方法呼叫：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing 會自動重新執行失敗的測試方法，並更新程式碼視窗和**測試總管**中的結果，如下圖所示：

    ![成功 HasEmbeddedSpaces 測試。](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 查看 `HasEmbeddedSpaces` 方法中的比較。 它會將內嵌空格視為 U+0020。 不過，Unicode Standard 包含許多其他空格字元。 這可能表示不正確地測試程式庫程式碼的空格字元。

1. 將相等比較取代為 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 方法呼叫：

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing 會自動重新執行失敗的測試方法，並更新程式碼視窗和**測試總管**中的結果，如下圖所示：

    ![成功 HasEmbeddedSpaces 測試。](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing 常見問題集](live-unit-testing-faq.md)