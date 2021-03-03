---
title: 了解如何使用 Live Unit Test 來測試程式碼
description: 藉由建立以 .NET Standard 為目標的簡單類別庫，並建立以 .NET Core 為目標的 MSTest 專案來進行測試，以瞭解如何使用即時單元測試。
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: d411465869cc960631063d09752d38536af94119
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683611"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing 的使用者入門

當您在 Visual Studio 方案中啟用即時單元測試時，它會以視覺化方式呈現您的測試涵蓋範圍和測試狀態。 當您修改程式碼時，即時單元測試也會動態地執行測試，並在您的變更導致測試失敗時立即通知您。

您可以使用即時單元測試來測試以 .NET Framework 或 .NET Core 為目標的方案。 在本教學課程中，您將瞭解如何藉由建立以 .NET Standard 為目標的簡單類別庫來使用即時單元測試，並建立以 .NET Core 為目標的 MSTest 專案以進行測試。

您可以從 GitHub 的 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) 存放庫下載完整 C# 方案。

## <a name="prerequisites"></a>必要條件

本教學課程需要您已安裝具有 **.Net Core 跨平臺開發** 工作負載的 Visual Studio Enterprise edition。

## <a name="create-the-solution-and-the-class-library-project"></a>建立方案和類別庫專案

首先，建立名為 UtilityLibraries 的 Visual Studio 方案，其中包含單一的 .NET Standard 類別庫專案 StringLibrary。

方案只是一或多個專案的容器。 若要建立空白方案，請開啟 Visual Studio 並執行下列作業：

1.   >    >  從最上層的 Visual Studio 功能表中，選取 [檔案新 **專案**]。

1. 在範本搜尋方塊中鍵入 [方案]，然後選取 [空白方案] 範本。 將專案命名為 **UtilityLibraries**。

   ::: moniker range="vs-2017"

   ![[新增專案] 對話方塊](./media/lut-start/new-solution.png)

   ::: moniker-end

1. 完成建立方案。

現在您已建立解決方案，您將建立名為 StringLibrary 的類別庫，其中包含一些用於處理字串的擴充方法。

1. 在 [**方案 Explorer**] 中，以滑鼠右鍵按一下 UtilityLibraries 方案，然後選取 [**加入**  >  **新專案**]。

::: moniker range="vs-2017"

2. 在 [新增專案] 對話方塊中，選取 C# 節點，然後選取 [.NET Standard]。

   > [!NOTE]
   > 因為我們的程式庫是以 .NET Standard 為目標，而不是特定的 .NET 執行，所以可以從支援該 .NET Standard 版本的任何 .NET 執行呼叫。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

3. 在右窗格中選取 [ **.Net Standard) 範本 ( 類別庫**，並在 [**名稱**] 文字方塊中輸入 **StringLibrary** ，如下圖所示：

   ![[新增專案] 對話方塊](./media/lut-start/add-project-cs.png)

4. 選取 [確定] 可建立專案。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在範本的搜尋方塊中鍵入 **類別庫**，然後選取 [類別庫 (.NET Standard)] 範本。 按一下 [下一步] 。

   > [!NOTE]
   > 因為我們的程式庫是以 .NET Standard 為目標，而不是特定的 .NET 執行，所以可以從支援該 .NET Standard 版本的任何 .NET 執行呼叫。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

3. 將專案命名為 **StringLibrary**。

4. 按一下 [建立]  以建立專案。

::: moniker-end

5. 以下列程式碼取代程式碼編輯器中的所有現有程式碼：

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary 有三種靜態方法：

   - 如果字串的開頭是大寫字元，則 `StartsWithUpper` 會傳回 `true`；否則會傳回 `false`。

   - 如果字串的開頭是小寫字元，則 `StartsWithLower` 會傳回 `true`；否則會傳回 `false`。

   - 如果字串包含內嵌空白字元，則 `HasEmbeddedSpaces` 會傳回 `true`；否則會傳回 `false`。

6.   >  從最上層的 Visual Studio 功能表中選取 [組建 **組建方案**]。 組建應該會成功。

## <a name="create-the-test-project"></a>建立測試專案

下一步是建立單元測試專案來測試 StringLibrary 程式庫。 執行下列步驟，以建立單元測試：

1. 在 [**方案 Explorer**] 中，以滑鼠右鍵按一下 UtilityLibraries 方案，然後選取 [**加入**  >  **新專案**]。

::: moniker range="vs-2017"

2. 在 [新增專案] 對話方塊中，選取 C# 節點，然後選取 [.NET Core]。

   > [!NOTE]
   > 您不需要使用與類別庫相同的語言來撰寫單元測試。

3. 在右窗格中選取 [ **( .Net Core) 範本的單元測試專案**]，然後在 [**名稱**] 文字方塊中輸入 **StringLibraryTests** ，如下圖所示：

   ![單元測試專案的 [新增專案] 對話方塊](./media/lut-start/add-unit-test-cs.png)

4. 選取 [確定] 可建立專案。

   > [!NOTE]
   > 本入門教學課程會搭配使用 Live Unit Testing 與 MSTest 測試架構。 您也可以使用 xUnit 和 NUnit 測試架構。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [範本搜尋] 方塊中輸入 **單元測試** ，選取 **c #** 做為語言，然後選取 [.net Core] 範本的 **單元測試專案** 。 按一下 [下一步] 。

   > [!NOTE]
   > 從 Visual Studio 2019 版本16.9 開始，MSTest 專案範本名稱從 **Mstest 單元測試專案 ( .Net Core)** 變更為 **單元測試專案**。

3. 將專案命名為 **StringLibraryTests** ，然後按 **[下一步]**。

4. 選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。

   > [!NOTE]
   > 本入門教學課程會搭配使用 Live Unit Testing 與 MSTest 測試架構。 您也可以使用 xUnit 和 NUnit 測試架構。

::: moniker-end

5. 單元測試專案無法自動存取所測試的類別程式庫。 您可以新增類別庫專案的參考，以提供測試程式庫存取權。 若要這樣做，請以滑鼠右鍵按一下 `StringLibraryTests` 專案，然後選取 [**加入**  >  **參考**]。 在 [ **參考管理員** ] 對話方塊中，確認已選取 [ **方案** ] 索引標籤，然後選取 StringLibrary 專案，如下圖所示。

   ![[參考管理員] 對話方塊](./media/lut-start/add-reference.png)

6. 將範本所提供的未定案單元測試程式碼取代為下列程式碼：

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. 選取工具列上的 **儲存** 圖示，以儲存專案。

   因為單元測試程式碼包含一些非 ASCII 字元，所以您會看到下列對話方塊，以警告當您將檔案儲存為預設 ASCII 格式時，某些字元將會遺失。

8. 選擇 [用其他編碼儲存] 按鈕。

   ![選擇檔案編碼](media/lut-start/ascii-encoding.png)

9. 在 [**預先儲存選項**] 對話方塊的 [**編碼**] 下拉式清單中，選擇 [ **Unicode (不含簽章的 utf-8) -字碼頁 65001**]，如下圖所示：

   ![選擇 UTF-8 編碼](media/lut-start/utf8-encoding.png)

10.   >  從最上層 Visual Studio 功能表中選取 [組建 **重建方案**]，以編譯單元測試專案。

您已為其建立類別庫以及一些單元測試。 您現在已完成使用 Live Unit Testing 所需的準備工作。

## <a name="enable-live-unit-testing"></a>啟用 Live Unit Testing

到目前為止，雖然您已撰寫 StringLibrary 類別庫的測試，但尚未執行這些測試。 Live Unit Testing 會在啟用之後自動執行它們。 若要這麼做，請執行下列作業：

1. （選擇性）選取包含 StringLibrary 程式碼的 [程式碼編輯器] 視窗。 這會針對 c # 專案 *Class1.cs* ，或針對 Visual Basic 專案為 *Class1。*  (此步驟可讓您在啟用即時單元測試之後，以視覺化方式檢查測試結果和程式碼涵蓋範圍的範圍。 ) 

1.   >    >  從最上層的 Visual Studio 功能表中，選取 [從最上層 Visual Studio **開始** 測試即時單元測試]。

1. Visual Studio 會啟動 Live Unit Test，以自動執行所有測試。

::: moniker range="vs-2017"
完成執行測試之後，**測試總管** 會顯示整體結果和個別測試結果。 此外，[程式碼編輯器] 視窗會以圖形方式顯示測試程式碼涵蓋範圍和測試結果。 如下圖所示，所有三項測試都已成功執行。 它也會顯示我們的測試已涵蓋 `StartsWithUpper` 方法中的所有程式碼路徑，而且已成功執行這些測試 (以綠色核取記號 "✓" 指出)。 最後，它會顯示 StringLibrary 中的其他方法都沒有程式碼涵蓋範圍 (，以藍色線 "➖" ) 表示。

![啟動即時單元測試之後的 [測試瀏覽器] 和 [程式碼編輯器] 視窗](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
當測試完成執行您的測試時， **即時單元測試** 會顯示整體結果和個別測試的結果。 此外，[程式碼編輯器] 視窗會以圖形方式顯示測試程式碼涵蓋範圍和測試結果。 如下圖所示，所有三項測試都已成功執行。 它也會顯示我們的測試已涵蓋 `StartsWithUpper` 方法中的所有程式碼路徑，而且已成功執行這些測試 (以綠色核取記號 "✓" 指出)。 最後，它會顯示 StringLibrary 中的其他方法都沒有程式碼涵蓋範圍 (，以藍色線 "➖" ) 表示。

![啟動即時單元測試之後的 [即時測試瀏覽器] 和 [程式碼編輯器] 視窗](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

您也可以在 [程式碼編輯器] 視窗中選取特定的程式碼涵蓋範圍圖示，以取得測試涵蓋範圍和測試結果的詳細資訊。 若要檢查此詳細資料，請執行下列作業：

1. 按一下 `StartsWithUpper` 方法之 `if (String.IsNullOrWhiteSpace(s))` 行中的綠色核取記號。 如下圖所示，即時單元測試表示三項測試涵蓋該程式程式碼，而且全部都已成功執行。

   !['if' 條件陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs1.png)

1. 按一下 `StartsWithUpper` 方法之 `return Char.IsUpper(s[0])` 行中的綠色核取記號。 如下圖所示，即時單元測試表示只有兩個測試涵蓋該程式程式碼，而且全部都已成功執行。

   ![return 陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs2.png)

Live Unit Testing 所識別的主要問題是不完整的程式碼涵蓋範圍。 您將在下節中解決它。

## <a name="expand-test-coverage"></a>展開測試涵蓋範圍

在本節中，您會將單元測試擴充至 `StartsWithLower` 方法。 當您這麼做時，Live Unit Testing 會動態繼續測試您的程式碼。

若要將程式碼涵蓋範圍擴充至 `StartsWithLower` 方法，請執行下列作業：

1. 將下列 `TestStartsWithLower` 和 `TestDoesNotStartWithLower` 方法新增至專案的測試原始程式檔：

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. 藉 `DirectCallWithNullOrEmpty` 由在呼叫方法之後立即新增下列程式碼來修改方法 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) 。

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing 會在您修改原始程式碼時自動執行新的和修改過的測試。 如下圖所示，所有測試（包括您已新增的兩個測試，以及您修改過的所有測試）都已成功。

   ::: moniker range="vs-2017"
   ![展開測試涵蓋範圍之後的 Test Explorer](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![展開測試涵蓋範圍之後的即時測試瀏覽器](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. 切換至包含 StringLibrary 類別之原始程式碼的視窗。 Live Unit Testing 現在會顯示我們的程式碼涵蓋範圍擴充至 `StartsWithLower` 方法。

    ![StartsWithLower 方法的程式碼涵蓋範圍](media/lut-start/lut-extended-cs.png)

在某些情況下， **測試瀏覽器** 中的成功測試可能會呈現灰色。這表示測試目前正在執行，或測試尚未再次執行，因為沒有任何程式碼變更會影響自上次執行後的測試。

截至目前為止，所有測試均為成功。 在下節中，我們將檢查如何處理測試失敗。

## <a name="handle-a-test-failure"></a>處理測試失敗

在本節中，您將探索如何使用 Live Unit Testing 來識別、疑難排解和解決測試失敗。 做法是將測試涵蓋範圍展開至 `HasEmbeddedSpaces` 方法。

1. 將下列方法新增至測試檔案：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. 當測試執行時，即時單元測試會指出 `TestHasEmbeddedSpaces` 方法已失敗，如下圖所示：

   ::: moniker range="vs-2017"
   ![測試瀏覽器報告失敗的測試](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Live Test Explorer 報告測試失敗](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. 選取顯示程式庫程式碼的視窗。 Live Unit 測試已擴充方法的程式碼涵蓋範圍 `HasEmbeddedSpaces` 。 它也會在失敗測試所涵蓋的程式行中新增紅色 "🞩"，以報告測試失敗。

1. 將游標停留在含 `HasEmbeddedSpaces` 方法簽章的行上方。 Live Unit 測試會顯示一個工具提示，報告該方法是否由一個測試所涵蓋，如下圖所示：

   ![測試失敗的即時單元測試資訊](media/lut-start/test-failure-info-cs.png)

1. 選取失敗的 **TestHasEmbeddedSpaces** 測試。 即時單元測試提供您幾個選項，例如執行所有測試和所有測試的測試，如下圖所示：

   ::: moniker range="vs-2017"
   ![測試失敗的即時單元測試選項](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![測試失敗的即時單元測試選項](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. 選取 [ **全部調試** ] 以偵測失敗的測試。

1. Visual Studio 會以偵錯模式執行測試。

   測試會將陣列中的每個字串指派給名為的變數 `phrase` ，並將它傳遞給 `HasEmbeddedSpaces` 方法。 assert 運算式第一次為 `false` 時，執行程式會暫停並叫用偵錯工具。 下圖顯示由方法呼叫中非預期值所產生的例外狀況對話方塊 [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) 。

   ![Live Unit 測試例外狀況對話方塊](media/lut-start/exception-dialog-cs.png)

   此外，Visual Studio 提供的所有偵錯工具都可協助我們疑難排解失敗的測試，如下圖所示：

   ![Visual Studio 調試工具](media/lut-start/debugging-tools-cs.png)

   請注意，在 `phrase` 變數值為 "Name\tDescription" (即陣列的第二個項目) 的 [自動變數] 視窗中。 測試方法預期 `HasEmbeddedSpaces` 在收到此字串時傳回 `true`；但卻傳回 `false`。 顯然，它無法將 "\t" (定位字元) 辨識為內嵌空格。

1. 選取 [ **Debug**  >  **Continue**]、按 **F5**，或按一下工具列上的 [**繼續**] 按鈕，繼續執行測試程式。 因為發生無法處理的例外狀況，所以測試終止。
這提供初步調查 Bug 的足夠資訊。 `TestHasEmbeddedSpaces` (測試常式) 的假設錯誤，或 `HasEmbeddedSpaces` 未正確地辨識所有內嵌空格。

1. 若要診斷並修正問題，請從 `StringLibrary.HasEmbeddedSpaces` 方法著手。 查看 `HasEmbeddedSpaces` 方法中的比較。 它會將內嵌空格視為 U+0020。 不過，Unicode Standard 包含許多其他空格字元。 這可能表示不正確地測試程式庫程式碼的空格字元。

1. 將相等比較取代為 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 方法呼叫：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. 即時單元測試會自動重新運行失敗的測試方法。

   即時單元測試會顯示更新後的結果，這也會出現在 [程式碼編輯器] 視窗中。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing 常見問題集](live-unit-testing-faq.md)
