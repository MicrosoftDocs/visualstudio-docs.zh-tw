---
title: 了解如何使用 Live Unit Test 來測試程式碼
ms.date: 04/03/2020
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2abc8eaaca923435620148d7313c6cc422bd1870
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697306"
---
# <a name="get-started-with-live-unit-testing"></a>Live Unit Testing 的使用者入門

在 Visual Studio 解決方案中啟用即時單元測試時,它會直觀地描述您的測試覆蓋率和測試的狀態。 即時單元測試還會在修改代碼時動態執行測試,並在更改導致測試失敗時立即通知您。

即時單元測試可用於測試針對 .NET 框架或 .NET 核心的解決方案。 在本教學中,您將透過建立面向 .NET 標準的簡單類庫來學習使用即時單元測試,您將創建一個針對 .NET Core 的 MSTest 專案來測試它。

您可以從 GitHub 的 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) 存放庫下載完整 C# 方案。

## <a name="prerequisites"></a>Prerequisites

本教程要求您安裝了帶有 **.NET Core 跨平台開發工作負載的**Visual Studio 企業版。

## <a name="create-the-solution-and-the-class-library-project"></a>建立方案和類別庫專案

首先創建名為實用程式庫的可視化工作室解決方案,該解決方案由單個 .NET 標準類庫專案 StringLibrary 組成。

方案只是一或多個專案的容器。 若要建立空白方案，請開啟 Visual Studio 並執行下列作業：

1. **從頂級**可視化工作室功能表中選擇 **「檔** > **新專案** > 」。

1. 在範本搜尋方塊中鍵入 [方案]****，然後選取 [空白方案]**** 範本。 命名項目**公用程式庫**。

   ::: moniker range="vs-2017"

   ![[新增專案] 對話方塊](./media/lut-start/new-solution.png)

   ::: moniker-end

1. 完成建立方案。

現在,您已經創建了解決方案,您將創建一個名為 StringLibrary 的類庫,其中包含許多用於處理字串的擴展方法。

1. 在**解決方案資源管理器中**,右鍵按一下實用程式庫解決方案並選擇「**新增新** > **專案**」。

::: moniker range="vs-2017"

2. 在 [新增專案]**** 對話方塊中，選取 C# 節點，然後選取 [.NET Standard]****。

   > [!NOTE]
   > 由於我們的庫以 .NET 標準為目標,而不是特定的 .NET 實現,因此可以從支援 .NET 標準版本的任何 .NET 實現調用它。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

3. 在右側窗格中選擇**類庫 (.NET 標準)** 範本,並在 **「名稱**」文本框中輸入**StringLibrary,** 如下圖所示:

   ![[新增專案] 對話方塊](./media/lut-start/add-project-cs.png)

4. 選取 [確定]**** 可建立專案。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在範本的搜尋方塊中鍵入**類別庫**，然後選取 [類別庫 (.NET Standard)]**** 範本。 按 [下一步]  。

   > [!NOTE]
   > 由於我們的庫以 .NET 標準為目標,而不是特定的 .NET 實現,因此可以從支援 .NET 標準版本的任何 .NET 實現調用它。 如需詳細資訊，請參閱 [.NET Standard](/dotnet/standard/net-standard)。

3. 命名項目**字串庫**。

4. 按一下 [建立]**** 以建立專案。

::: moniker-end

5. 將代碼編輯器中的所有現有代碼取代為以下代碼:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   字串庫有三種靜態方法:

   - 如果字串的開頭是大寫字元，則 `StartsWithUpper` 會傳回 `true`；否則會傳回 `false`。

   - 如果字串的開頭是小寫字元，則 `StartsWithLower` 會傳回 `true`；否則會傳回 `false`。

   - 如果字串包含內嵌空白字元，則 `HasEmbeddedSpaces` 會傳回 `true`；否則會傳回 `false`。

6. 從頂級可視化工作室功能表中選擇 > **「生成生成解決方案**」。 **Build** 生成應成功。

## <a name="create-the-test-project"></a>建立測試專案

下一步是創建單元測試專案以測試 StringLibrary 庫。 執行下列步驟，以建立單元測試：

1. 在**解決方案資源管理器中**,右鍵按一下實用程式庫解決方案並選擇「**新增新** > **專案**」。

::: moniker range="vs-2017"

2. 在 [新增專案]**** 對話方塊中，選取 C# 節點，然後選取 [.NET Core]****。

   > [!NOTE]
   > 您不需要使用與類別庫相同的語言來撰寫單元測試。

3. 在右側窗格中選擇 **「單元測試專案 (.NET Core)」** 範本,並在 **「名稱 」** 文本框中輸入**StringLibrary 測試**,如下圖所示:

   ![單元測試專案的 [新增專案] 對話方塊](./media/lut-start/add-unit-test-cs.png)

4. 選取 [確定]**** 可建立專案。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在範本搜尋框中鍵入**單元測試**,然後選擇**MSTest 測試專案 (.NET Core)** 範本。 按 [下一步]  。

3. 命名項目**字串函式庫測試**。

4. 按一下 [建立]**** 以建立專案。

::: moniker-end

   > [!NOTE]
   > 本入門教學課程會搭配使用 Live Unit Testing 與 MSTest 測試架構。 您也可以使用 xUnit 和 NUnit 測試架構。

5. 單元測試專案無法自動存取所測試的類別程式庫。 您可以新增類別庫專案的參考，以提供測試程式庫存取權。 為此,請右鍵單擊`StringLibraryTests`項目並選擇「**添加** > **參考**」。 在**參考管理器**對話方塊中,請確保選擇了 **「解決方案**」選項卡,並選擇 StringLibrary 專案,如下圖所示。

   ![[參考管理員] 對話方塊](./media/lut-start/add-reference.png)

6. 將範本所提供的未定案單元測試程式碼取代為下列程式碼：

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. 選取工具列上的**儲存**圖示，以儲存專案。

   由於單元測試代碼包含一些非 ASCII 字元,因此您將看到以下對話方塊,以警告如果以預設 ASCII 格式保存檔,某些字元將丟失。

8. 選擇 [用其他編碼儲存]**** 按鈕。

   ![選擇檔案編碼](media/lut-start/ascii-encoding.png)

9. 在 **「提前儲存選項」** 對話框的 **「編碼**」 「下拉清單中,選擇**Unicode(UTF-8,無簽名) - 代碼頁 65001,** 如下圖所示:

   ![選擇 UTF-8 編碼](media/lut-start/utf8-encoding.png)

10. 通過從頂級可視化工作室功能表中選擇**生成** > **重建解決方案**來編譯單元測試專案。

您已為其建立類別庫以及一些單元測試。 您現在已完成使用 Live Unit Testing 所需的準備工作。

## <a name="enable-live-unit-testing"></a>啟用 Live Unit Testing

到目前為止,儘管您已為 StringLibrary 類庫編寫了測試,但尚未執行這些測試。 Live Unit Testing 會在啟用之後自動執行它們。 若要這麼做，請執行下列作業：

1. 或者,選擇包含 StringLibrary 代碼的代碼編輯器視窗。 這要麼是 C# 專案的*Class1.cs,* 要麼是 Visual Basic 專案的*Class1.vb。* (此步驟允許您在啟用即時單元測試後直觀地檢查測試結果和代碼覆蓋率。

1. 從頂級可視化工作室功能表中選擇 **「測試** > **即時單元測試** > **開始**」。

1. Visual Studio 會啟動 Live Unit Test，以自動執行所有測試。

::: moniker range="vs-2017"
完成執行測試之後，**測試總管**會顯示整體結果和個別測試結果。 此外,代碼編輯器視窗以圖形方式顯示測試代碼覆蓋率和測試結果。 如下圖所示,所有三個測試都已成功執行。 它也會顯示我們的測試已涵蓋 `StartsWithUpper` 方法中的所有程式碼路徑，而且已成功執行這些測試 (以綠色核取記號 "✓" 指出)。 最後,它表明 StringLibrary 中的其他方法都沒有代碼覆蓋率(由藍線"➖"表示)。

![啟動即時單元測試後測試資源管理員與代碼編輯器視窗](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
執行完測試後,**即時單元測試**將顯示總體結果和單個測試的結果。 此外,代碼編輯器視窗以圖形方式顯示測試代碼覆蓋率和測試結果。 如下圖所示,所有三個測試都已成功執行。 它也會顯示我們的測試已涵蓋 `StartsWithUpper` 方法中的所有程式碼路徑，而且已成功執行這些測試 (以綠色核取記號 "✓" 指出)。 最後,它表明 StringLibrary 中的其他方法都沒有代碼覆蓋率(由藍線"➖"表示)。

![啟動即時單元測試後的即時測試資源管理員與程式碼編輯器視窗](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

您還可以透過在程式碼編輯器視窗中選擇特定代碼覆蓋率圖示來取得有關測試覆蓋率和測試結果的更多詳細資訊。 若要檢查此詳細資料，請執行下列作業：

1. 按一下 `StartsWithUpper` 方法之 `if (String.IsNullOrWhiteSpace(s))` 行中的綠色核取記號。 如下圖所示,Live 單元測試指示三個測試涵蓋該代碼行,並且所有測試都已成功執行。

   !['if' 條件陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs1.png)

1. 按一下 `StartsWithUpper` 方法之 `return Char.IsUpper(s[0])` 行中的綠色核取記號。 如下圖所示,Live 單元測試指示只有兩個測試涵蓋該代碼行,並且所有測試都已成功執行。

   ![return 陳述式的程式碼涵蓋範圍](media/lut-start/code-coverage-cs2.png)

Live Unit Testing 所識別的主要問題是不完整的程式碼涵蓋範圍。 您將在下節中解決它。

## <a name="expand-test-coverage"></a>展開測試涵蓋範圍

在本節中，您會將單元測試擴充至 `StartsWithLower` 方法。 當您這麼做時，Live Unit Testing 會動態繼續測試您的程式碼。

若要將程式碼涵蓋範圍擴充至 `StartsWithLower` 方法，請執行下列作業：

1. 將下列 `TestStartsWithLower` 和 `TestDoesNotStartWithLower` 方法新增至專案的測試原始程式檔：

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. `DirectCallWithNullOrEmpty`通過在調用 方法后立即添加以下代碼[`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse)來 修改方法。

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing 會在您修改原始程式碼時自動執行新的和修改過的測試。 如下圖所示,所有測試(包括已添加的兩個測試和已修改的測試)都已成功。

   ::: moniker range="vs-2017"
   ![延伸測試範圍後測試資源管理員](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![延伸測試範圍後的即時測試資源管理員](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. 切換到包含 StringLibrary 類源代碼的視窗。 Live Unit Testing 現在會顯示我們的程式碼涵蓋範圍擴充至 `StartsWithLower` 方法。

    ![StartsWithLower 方法的程式碼涵蓋範圍](media/lut-start/lut-extended-cs.png)

在某些情況下,**測試資源管理器**中的成功測試可能灰顯。這表示測試當前正在執行,或者測試沒有再次運行,因為自上次執行測試以來,沒有代碼更改會影響測試。

截至目前為止，所有測試均為成功。 在下節中，我們將檢查如何處理測試失敗。

## <a name="handle-a-test-failure"></a>處理測試失敗

在本節中，您將探索如何使用 Live Unit Testing 來識別、疑難排解和解決測試失敗。 做法是將測試涵蓋範圍展開至 `HasEmbeddedSpaces` 方法。

1. 將下列方法新增至測試檔案：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. 測試執行時,即時單元測試指示`TestHasEmbeddedSpaces`該方法失敗,如下圖所示:

   ::: moniker range="vs-2017"
   ![測試資源管理員回報測試失敗](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![即時測試資源管理員回報測試失敗](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. 選取顯示程式庫程式碼的視窗。 即時單元測試將代碼覆蓋率擴展到該方法`HasEmbeddedSpaces`。 它也會在失敗測試所涵蓋的程式行中新增紅色 "🞩"，以報告測試失敗。

1. 將游標停留在含 `HasEmbeddedSpaces` 方法簽章的行上方。 即時單元測試顯示一個工具提示,用於報告該方法由一個測試覆蓋,如下圖所示:

   ![失敗測試的即時儲存測試資訊](media/lut-start/test-failure-info-cs.png)

1. 選取失敗的 **TestHasEmbeddedSpaces** 測試。 即時單元測試提供了幾個選項,例如運行所有測試和調試所有測試,如下圖所示:

   ::: moniker range="vs-2017"
   ![失敗測試的即時儲存測試選項](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![失敗測試的即時儲存測試選項](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. 選擇 **「全部除錯」** 以除錯失敗的測試。

1. Visual Studio 會以偵錯模式執行測試。

   測試將陣列中的每個字串分配給一個變數,`phrase`並將其傳遞給`HasEmbeddedSpaces`方法。 assert 運算式第一次為 `false` 時，執行程式會暫停並叫用偵錯工具。 方法調用中[`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue)意外值產生的異常對話框如下圖所示。

   ![即時單元測試異常對話框](media/lut-start/exception-dialog-cs.png)

   此外,Visual Studio 提供的所有調試工具都可用於幫助我們解決失敗的測試,如下圖所示:

   ![視覺化工作室除錯工具](media/lut-start/debugging-tools-cs.png)

   請注意，在 `phrase` 變數值為 "Name\tDescription" (即陣列的第二個項目) 的 [自動變數]**** 視窗中。 測試方法預期 `HasEmbeddedSpaces` 在收到此字串時傳回 `true`；但卻傳回 `false`。 顯然，它無法將 "\t" (定位字元) 辨識為內嵌空格。

1. 選擇 **「調試** > **繼續**」,按**F5,** 或單擊工具列上的 **「繼續」** 按鈕以繼續執行測試程式。 因為發生無法處理的例外狀況，所以測試終止。
這提供初步調查 Bug 的足夠資訊。 `TestHasEmbeddedSpaces` (測試常式) 的假設錯誤，或 `HasEmbeddedSpaces` 未正確地辨識所有內嵌空格。

1. 要診斷和更正問題,請從方法`StringLibrary.HasEmbeddedSpaces`開始。 查看 `HasEmbeddedSpaces` 方法中的比較。 它會將內嵌空格視為 U+0020。 不過，Unicode Standard 包含許多其他空格字元。 這可能表示不正確地測試程式庫程式碼的空格字元。

1. 將相等比較取代為 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 方法呼叫：

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. 即時單元測試會自動重新運行失敗的測試方法。

   即時單元測試顯示更新的結果,該結果也顯示在代碼編輯器視窗中。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing 常見問題集](live-unit-testing-faq.md)
