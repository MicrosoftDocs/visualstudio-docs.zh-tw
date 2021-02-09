---
title: 使用從使用方式產生的測試優先開發
description: 瞭解如何透過使用 [從使用量產生] 功能來合併測試優先的開發方法。
ms.custom: SEO-VS-2020
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: how-to
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4ea04a9c70f23c30a5f603fa9411780223fff563
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883047"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>逐步解說：以使用時產生功能進行測試優先開發

本主題示範如何使用 [Generate From Usage](../ide/visual-csharp-intellisense.md#generate-from-usage) 功能，支援「測試先行」開發方式。

 *「測試先行」開發方式* (Test-first development) 這種軟體設計方法，要先根據產品規格撰寫單元測試，再撰寫測試成功所需要的原始程式碼。 Visual Studio 支援測試先行開發方式的做法是，當您第一次在測試案例中參考類型和成員時，先以原始程式碼產生新的類型和成員，再定義它們。

Visual Studio 在盡可能不中斷工作流程的情況下產生新的類型和成員。 您可以建立類型、方法、屬性、欄位或建構函式的 Stub，但不離開目前所在的程式碼位置。 當您開啟對話方塊指定類型產生選項時，焦點會在對話方塊一關閉時，立即回到目前開啟的檔案。

[ **從使用量產生** ] 功能可以搭配與 Visual Studio 整合的測試架構一起使用。 本主題會示範 Microsoft 單元測試架構。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>建立 Windows 類別庫專案和測試專案

1. 在 C# 或 Visual Basic 中，建立新的 **Windows 類別庫** 專案。 將其命名為 `GFUDemo_VB` 或 `GFUDemo_CS`，視所用語言而定。

2. 在 [方案總管] 中，以滑鼠右鍵按一下上方的方案，選擇 [新增] > [新增專案]。

3. 建立新的 **單元測試專案 (.NET Framework)** 專案。

   ::: moniker range="vs-2017"

   下圖顯示 C# 範本的 [新增專案] 對話方塊。

   ![單元測試專案範本](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>在類別庫專案中新增參考

1. 在 **方案總管** 中，以滑鼠右鍵按一下單元測試專案下的 [參考] 項目，並選擇 [加入參考]。

2. 在 [參考管理員] 對話方塊中，選取 [專案]，然後選取類別庫專案。

3. 選擇 [確定] 以關閉 [參考管理員] 對話方塊。

4. 儲存您的方案。 您已準備好開始撰寫測試。

### <a name="generate-a-new-class-from-a-unit-test"></a>從單元測試產生新類別

1. 測試專案包含名為 *UnitTest1* 的檔案。 在 **方案總管** 中按兩下這個檔案，在程式碼編輯器中開啟它。 已產生測試類別和測試方法。

2. 找到類別 `UnitTest1` 的宣告，並將它重新命名為 `AutomobileTest`。

   > [!NOTE]
   > IntelliSense 提供兩種完成 IntelliSense 陳述式的方式： *完成模式* (completion mode) 和 *建議模式*(suggestion mode)。 當類別和成員在使用前即已定義的情況下，請使用建議模式。 當 [IntelliSense] 視窗開啟時，您可以按 **Ctrl**+**Alt**+**空格鍵** 切換完成模式和建議模式。 如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。 當您在下個步驟輸入 `Automobile` 時，建議模式非常有幫助。

3. 找到 `TestMethod1()` 方法並將它重新命名為 `DefaultAutomobileIsInitializedCorrectly()`。 在這個方法內，建立名為 `Automobile` 的類別新執行個體，如下列螢幕擷取畫面所示。 波浪底線隨即出現，這表示發生編譯時期錯誤，如果滑鼠停留在上面，[快速動作](../ide/quick-actions.md)錯誤燈泡會出現在左邊界或波浪線正下方。

    ![Visual Basic 中的快速動作](../ide/media/genclass_underlinevb.png)

    ![C&#35; 中的快速動作](../ide/media/genclass_underline.png)

4. 選擇或按一下 [ **快速動作** ] 燈泡。 您會看到錯誤訊息，說明類型 `Automobile` 未定義。 您也會看到一些解決方案。

5. 按一下 [ **產生新的類型** ]，開啟 [ **產生類型** ] 對話方塊。 此對話方塊會提供許多選項，包括在不同的專案中產生類型。

6. 在 [專案] 清單中，按一下 [GFUDemo\_VB] 或 [GFUDemo_CS] 指示 Visual Studio 將檔案新增至類別庫專案，不是新增至測試專案。 如果尚未選取，請選擇 [建立新檔案]並將其命名為 *Automobile.cs* 或 *Automobile.vb*。

     ![[產生新的類型] 對話方塊](../ide/media/genotherdialog.png)

7. 按一下 [確定]  關閉對話方塊，並建立新的檔案。

8. 在 **方案總管** 中，查看 [ **GFUDemo_VB** ] 或 [ **GFUDemo_CS** 專案] 節點底下， *確認新的* [ *Automobile.cs* ] 或 [檔案]。 在程式碼編輯器中，焦點仍在 `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`，這可讓您以最少的中斷繼續撰寫測試。

### <a name="generate-a-property-stub"></a>產生屬性虛設常式
假設產品規格規定 `Automobile` 類別有兩個公用屬性，名為 `Model` 和 `TopSpeed`。 這些屬性必須由預設的建構函式以 `"Not specified"` 和 `-1` 的預設值來初始化。 以下的單元測試會驗證預設建構函式是否將屬性設定為正確的預設值。

1. 將下列程式碼新增至 `DefaultAutomobileIsInitializedCorrectly` 測試方法。

     [!code-csharp[VbTDDWalkthrough#1](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.cs)]
     [!code-vb[VbTDDWalkthrough#1](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_1.vb)]

2. 因為程式碼參考 `Automobile` 上兩個未定義的屬性，所以 `Model` 和 `TopSpeed` 下會顯示波浪線。 將滑鼠停留在 `Model` 上並選擇 [快速動作] 錯誤燈泡，然後選擇 [產生屬性 'Automobile.Model']。

3. 以同樣方式產生 `TopSpeed` 屬性的屬性 Stub。

     在 `Automobile` 類別中，會從內容正確推斷出新屬性的類型。

### <a name="generate-a-stub-for-a-new-constructor"></a>產生新建構函式的虛設常式
現在我們要建立一個測試方法，產生建構函式 stub 以初始化 `Model` 和 `TopSpeed` 屬性。 稍後，您會新增更多的程式碼以完成測試。

1. 請將下列其他測試方法加入您的 `AutomobileTest` 類別中。

     [!code-csharp[VbTDDWalkthrough#2](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.cs)]
     [!code-vb[VbTDDWalkthrough#2](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_2.vb)]

2. 按一下紅色波浪線下的 [快速動作] 錯誤燈泡，然後按一下 [在 'Automobile' 中產生建構函式]。

     請注意，在 `Automobile` 類別檔案中，新的建構函式已檢查建構函式呼叫中所使用的區域變數名稱，找到 `Automobile` 類別中具有相同名稱的屬性，並提供建構函式主體的程式碼將引數值儲存在 `Model` 和 `TopSpeed` 屬性中。

3. 產生新的建構函式後， `DefaultAutomobileIsInitializedCorrectly`的預設建構函式呼叫下會出現波浪底線。 錯誤訊息指出 `Automobile` 類別沒有任何建構函式採用零引數。 若要產生沒有任何參數的明確預設建構函式，請按一下 [快速動作] 錯誤燈泡，然後按一下 [在 'Automobile' 中產生建構函式]。

### <a name="generate-a-stub-for-a-method"></a>產生方法的虛設常式
假設規格規定，如果其 `Model` 和 `TopSpeed` 屬性設為預設值以外的值，新的 `Automobile` 就可以放入 `IsRunning` 狀態。

1. 請將下列各行加入 `AutomobileWithModelNameCanStart` 方法中。

     [!code-csharp[VbTDDWalkthrough#3](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.cs)]
     [!code-vb[VbTDDWalkthrough#3](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_3.vb)]

2. 按一下 `myAuto.Start` 方法呼叫的 [快速動作] 錯誤燈泡，然後按一下 [產生方法 'Automobile.Start']。

3. 按一下屬性的 [ **快速動作** ] 燈泡 `IsRunning` ，然後按一下 [ **產生屬性 ' IsRunning '**]。

     `Automobile` 類別現在包含名為 `Start()` 的方法，和名為 `IsRunning` 的屬性。

### <a name="run-the-tests"></a>執行測試

1. 在 [測試] 功能表上，選擇 [執行] > [所有測試]。

     [**執行**  >  **所有測試**] 命令會在針對目前方案所撰寫的任何測試架構中，執行所有測試。 在這個案例中，會有兩個測試，而且兩個測試都應該要失敗。 `DefaultAutomobileIsInitializedCorrectly` 測試失敗的原因是 `Assert.IsTrue` 條件傳回 `False`。 `AutomobileWithModelNameCanStart` 測試失敗的原因是 `Start` 類別的 `Automobile` 方法擲回例外狀況。

     下圖顯示 [測試結果]  視窗。

     ![失敗的測試結果](../ide/media/testsfailed.png)

2. 在 [測試結果] 視窗中，在每個測試結果資料列按兩下，移至每一項測試的位置。

### <a name="implement-the-source-code"></a>實作原始程式碼

1. 將下列程式碼加入預設建構函式中，讓 `Model`、 `TopSpeed` 和 `IsRunning` 屬性都初始化為正確的 `"Not specified"`、 `-1`和 `False` (C# 為 `false`) 預設值。

     [!code-csharp[VbTDDWalkthrough#5](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.cs)]
     [!code-vb[VbTDDWalkthrough#5](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_5.vb)]

2. 呼叫 `Start` 方法時，它應該只有在 `IsRunning` 或 `Model` 屬性設為預設值以外的值時，才將 `TopSpeed` 旗標設為 true。 從方法主體移除 `NotImplementedException` ，並加入下列程式碼。

     [!code-csharp[VbTDDWalkthrough#6](../ide/codesnippet/CSharp/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.cs)]
     [!code-vb[VbTDDWalkthrough#6](../ide/codesnippet/VisualBasic/walkthrough-test-first-support-with-the-generate-from-usage-feature_6.vb)]

### <a name="run-the-tests-again"></a>再次執行測試

- 在 [測試] 功能表中指向 [執行]，然後按一下 [所有測試]。

     測試這一次會成功。 下圖顯示 [測試結果]  視窗。

     ![成功的測試結果](../ide/media/testspassed.png)

## <a name="see-also"></a>另請參閱

- [從使用量產生](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [使用 IntelliSense](../ide/using-intellisense.md)
- [對程式碼進行單元測試](../test/unit-test-your-code.md)
- [快速動作](../ide/quick-actions.md)
