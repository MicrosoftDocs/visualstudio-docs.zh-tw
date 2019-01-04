---
title: 使用使用者介面自動化來測試您的程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
ms.assetid: ad9e3eaa-ab86-436e-95b8-dc20eb1f8b2a
caps.latest.revision: 87
ms.author: gewarren
manager: douge
ms.openlocfilehash: c0a4ebdc99a416d46b9329137211a79d01700003
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804561"
---
# <a name="use-ui-automation-to-test-your-code"></a>使用 UI 自動化來測試您的程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

驅動應用程式通過其使用者介面 (UI) 的自動化測試稱為「自動程式化 UI 測試」(CUIT)。 這些測試包括 UI 控制項的功能測試。 它們可讓您確認整個應用程式 (包括其使用者介面) 正確運作。 自動程式碼 UI 測試特別適用於使用者介面中有驗證或其他邏輯時 (例如，在網頁中)。 它們也經常用來自動化現有手動測試。

 如下圖所示，一般的開發體驗可能是一開始您只是建置應用程式 (F5) 並按一下 UI 控制項確認所有項目都正確運作。 然後，您可能決定建立自動程式碼測試，因此不需要繼續手動測試應用程式。 根據您應用程式中測試的特定功能，您可以撰寫程式碼來進行功能測試或者也許包括 UI 層級測試的整合測試。 如果您只想要直接存取某個商務邏輯，則可以編寫單元測試。 不過，在特定情況下，也可能對測試您應用程式中的各種 UI 控制項有所助益。 自動程式化 UI 測試可以自動化初始 (F5) 情節，確認程式碼變換不會影響您應用程式的功能。

 ![在應用程式開發時進行測試](../test/media/cuit-overview.png "CUIT_Overview")

 建立自動程式化 UI 測試十分簡單。 您只要在背景執行 CUIT 測試產生器時手動執行測試即可。 您也可以指定特定欄位中應該出現的值。 CUIT 測試產生器會錄製您的動作，並透過這些動作產生程式碼。 建立測試之後，即可使用特殊編輯器來編輯該測試，以讓您修改動作的順序。

 或者，如果您在 Microsoft 測試管理員中錄製測試案例，則可以透過該測試案例產生程式碼。 如需詳細資訊，請參閱[記錄和播放手動測試](http://msdn.microsoft.com/library/9792e72f-600e-441f-9d4e-6510e5965665)。

 特殊 CUIT 測試產生器和編輯器可以輕鬆地建立與編輯自動程式化 UI 測試，即使您的主要技能是在測試，而非編寫程式碼也是一樣。 但是，如果您是開發人員，而且想要使用更進階的方式擴充測試，請讓程式碼更具結構性，以直接複製和調整。 例如，您可能錄製一個在網站上購買某項東西的測試，接著編輯產生的程式碼以加入購買許多項目的迴圈。

 **需求**

- Visual Studio 企業版

  如需自動程式化 UI 測試支援哪些平台和組態的詳細資訊，請參閱[支援的組態和平台自動程式化 UI 測試和動作記錄](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)。

  **本主題內容**

- [建立自動程式化 UI 測試](#VerifyingCodeUsingCUITCreate)

  -   [主要程序](#VerifyingCodeUsingCUITCreate)

  -   [啟動和停止應用程式](#starting)

  -   [驗證 UI 控制項的屬性](#VerifyingCodeUsingCUITGenerateAssertions)

- [自訂您的自動程式化 UI 測試](#VerifyingCodeCUITModify)

  -   [產生的程式碼](#generatedCode)

  -   [編寫 UI 控制項動作和屬性的程式碼](#actions)

  -   [偵錯](#debugging)

- [後續步驟](#VerifyCodeUsingCUITWhatsNext)

##  <a name="VerifyingCodeUsingCUITCreate"></a> 建立自動程式化 UI 測試

1. **建立自動程式化 UI 測試專案。**

    自動程式化 UI 測試必須包含在自動程式化 UI 測試專案中。 如果您還沒有自動程式化 UI 測試專案，請予以建立。 在 [方案總管] 的方案捷徑功能表上，依序選擇 [加入] 和 [新增專案]，然後選取 [Visual Basic] 或 [Visual C#]。 接著，依序選擇 [測試] 和 [自動程式化 UI 測試]。

   - <em>我看不到 [自動程式化 UI 測試] 專案範本。*

      您使用的 Visual Studio 版本可能不支援自動程式化 UI 測試。 若要建立自動程式化 UI 測試，您必須使用 Visual Studio Enterprise。

2. **加入自動程式化 UI 測試檔案。**

    如果您剛剛建立自動程式碼 UI 專案，則自動加入第一個 CUIT 檔案。 若要加入另一個測試檔案，請在自動程式化 UI 測試專案上開啟捷徑功能表，並指向 [加入]，然後選擇 [自動程式化 UI 測試]。

    ![建立自動程式化 UI 測試](../test/media/codedui-create.png "CodedUI_Create")

    在 [產生自動程式化 UI 測試的程式碼] 對話方塊中，選擇 [錄製動作、編輯 UI 對應或加入判斷提示]。

    ![選取錄製動作](../test/media/codedui-codegendialogb.png "CodedUI_CodeGenDialogB")

    [自動程式化 UI 測試產生器] 隨即顯示，並將 Visual Studio 最小化。

    ![自動程式化 UI 測試產生器](../test/media/codedui-testbuilder.png "CodedUI_TestBuilder")

3. **錄製一連串的動作**。

    **若要開始錄製**，請選擇 [錄製] 圖示。 執行您想要在應用程式中測試的動作 (包括在必要時啟動應用程式)。

    例如，如果您是測試 Web 應用程式，則可能會啟動瀏覽器，並巡覽到網站，然後登入應用程式。

    **若要暫停錄製** (例如，如果您需要處理傳入的電子郵件)，請選擇 [暫停]。

   > [!WARNING]
   >  將會錄製所有在桌面上執行的動作。 如果您執行的動作可能會導致在錄製中包括敏感性資料，則請暫停錄製。

    **若要刪除錯誤錄製的動作**，請選擇 [編輯動作]。

    **若要產生複寫動作的程式碼**，請選擇 [產生程式碼] 圖示，並輸入自動程式化 UI 測試方法的名稱和描述。

4. **確認 UI 欄位 (例如文字方塊) 中的值**。

    選擇自動程式化 UI 測試產生器中的 [加入判斷提示]，然後選擇您執行中應用程式內的 UI 控制項。 在顯示的屬性清單中選取屬性，例如，文字方塊中的 [文字]。 在捷徑功能表上，選擇 [加入判斷提示]。 在此對話方塊中，選取比較運算子、比較值和錯誤訊息。

    關閉判斷提示視窗，然後選擇 [產生程式碼]。

    ![自動程式化 UI 測試目標項目](../test/media/codedui-1.png "CodedUI_1")

   > [!TIP]
   >  在錄製動作與確認值之間替換。 在每串動作或驗證結束時產生程式碼。 如果您想要，則可以稍後插入新的動作和驗證。

    如需詳細資料，請參閱[驗證控制項屬性](#VerifyingCodeUsingCUITGenerateAssertions)。

5. **檢視產生的測試程式碼**。

    若要檢視產生的程式碼，請關閉 [UI 測試產生器] 視窗。 在此程式碼中，您可以看到您提供給每個步驟的名稱。 此程式碼位於您已建立的 CUIT 檔案中：

   ```csharp
   [CodedUITest]
   public class CodedUITest1
   { ...
     [TestMethod]
     public void CodedUITestMethod1()
     {
         this.UIMap.AddTwoNumbers();
         this.UIMap.VerifyResultValue();
         // To generate more code for this test, select
         // "Generate Code" from the shortcut menu.
     }
   }
   ```

6. **加入其他動作和判斷提示**。

    將游標放在測試方法中的適當點，然後在捷徑功能表上選擇 [產生自動程式化 UI 測試的程式碼]。 將會在該點插入新的程式碼。

7. **編輯測試動作和判斷提示的詳細資料**。

    開啟 UIMap.uitest。 此檔案會在自動程式化 UI 測試編輯器中開啟，而您可以在其中編輯所錄製的任何一串動作，以及編輯您的判斷提示。

    ![自動程式化 UI 測試編輯器](../test/media/cuit-editor-edit.png "CUIT_Editor_edit")

    如需詳細資訊，請參閱[使用自動程式化 UI 測試編輯器來編輯自動程式化 UI 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

8. **執行測試**。

    使用 [測試總管]，或開啟測試方法中的捷徑功能表，然後選擇 [執行測試]。 如需如何執行測試的詳細資訊，請參閱[使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)以及本主題結尾[後續動作](#VerifyCodeUsingCUITWhatsNext)小節中的*執行自動程式化 UI 測試的其他選項*。

   本主題中的其餘各節提供此程序中各步驟的更多詳細資料。

   如需更詳細的範例，請參閱[逐步解說：建立、 編輯和維護自動程式化的 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)。 在這個逐步解說中，您將建立簡單的 Windows Presentation Foundation (WPF) 應用程式，以示範如何建立、編輯和維護自動程式化 UI 測試。 本逐步解說提供解決方案用來修正各種因時間問題和控制項重構而中斷的測試。

###  <a name="starting"></a> 啟動和停止受測試的應用程式
 *我不想要分別針對每個測試啟動和停止應用程式、瀏覽器或資料庫。我要如何避免這麼做？*

-   ![必要條件](../test/media/prereq.png "Prereq") 如果您不想要錄製可啟動受測試應用程式的動作，則必須先啟動應用程式，再選擇 [錄製] 圖示。

-   ![必要條件](../test/media/prereq.png "Prereq")在測試結束時，會終止在其中執行測試的流程。 如果您已在測試中啟動應用程式，則通常會關閉該應用程式。  如果您不想要測試在結束時關閉應用程式，則必須將 .runsettings 檔案加入至方案，並使用 `KeepExecutorAliveAfterLegacyRun` 選項。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

-   ![必要條件](../test/media/prereq.png "Prereq") 您可以加入測試初始化方法 (透過 [TestInitialize] 屬性予以識別)，此方法會在每個測試方法開始時執行程式碼。 例如，您可以從 TestInitialize 方法啟動應用程式。

-   ![必要條件](../test/media/prereq.png "Prereq") 您可以加入測試清除方法 (透過 [TestCleanup] 屬性予以識別)，此方法會在每個測試方法結束時執行程式碼。 例如，可以從 TestCleanup 方法呼叫關閉應用程式的方法。

###  <a name="VerifyingCodeUsingCUITGenerateAssertions"></a> 驗證 UI 控制項的屬性
 您可以使用 [自動程式化 UI 測試產生器] 將使用者介面 (UI) 控制項加入測試的 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>，或產生可使用 UI 控制項判斷提示之驗證方法的程式碼。

 若要產生 UI 控制項的判斷提示，請選擇自動程式化 UI 測試產生器中的 [加入判斷提示] 工具，並將它拖曳至受測試應用程式上想要驗證是否正確的控制項。 有方塊括住控制項時，請放開滑鼠。 此控制類別碼會立即在 `UIMap.Designer.cs` 檔案中建立。

 ![自動程式化 UI 測試目標項目](../test/media/codedui-1.png "CodedUI_1")

 此控制項的屬性現在會列在 [加入判斷提示] 對話方塊中。

 另一種巡覽至特定控制項的方式，是選擇箭號 **(<<)** 展開 [UI 控制項對應] 的檢視。 若要尋找父控制項、同層級控制項或子控制項，您可以按一下對應中的任何位置，並使用方向鍵在樹狀目錄中移動。

 ![自動程式化 UI 測試屬性](../test/media/codedui-2.png "CodedUI_2")

- *我在選取應用程式中的控制項時看不到任何屬性，或者在 UI 控制項對應中看不到該控制項。*

   在應用程式程式碼中，您想要驗證的控制項必須要有唯一的 ID (例如 HTML ID 屬性) 或 WPF UId。 您可能需要更新應用程式程式碼以加入這些 ID。

  接下來，開啟想要驗證之 UI 控制項的屬性的捷徑功能表，然後指向 [加入判斷提示]。 在 [新增判斷提示] 對話方塊中，選取您判斷提示的 [比較子] (例如 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>)，然後在 [比較值] 中輸入您判斷提示的值。

  ![自動程式化 UI 測試判斷提示](../test/media/codedui-3.png "CodedUI_3")

  加入您測試的所有判斷提示之後，請選擇 [確定]。

  若要產生您判斷提示的程式碼，並將控制項加入至 UI 對應，請選擇 [產生程式碼] 圖示。 輸入您自動程式化 UI 測試方法的名稱以及該方法的描述，這些將加入為該方法的註解。 選擇 [加入並產生]。 接下來，選擇 [關閉] 圖示關閉 [自動程式化 UI 測試產生器]。 這樣會產生與下列程式碼類似的程式碼。 例如，如果您輸入的名稱是 `AssertForAddTwoNumbers`，則程式碼會與此範例類似：

- 將判斷提示方法 AssertForAddTwoNumbers 呼叫加入至您自動程式碼 UI 測試檔案中的測試方法：

  ```
  [TestMethod]
  public void CodedUITestMethod1()
  {
      this.UIMap.AddTwoNumbers();
      this.UIMap.AssertForAddTwoNumbers();
  }
  ```

   您可以編輯此檔案以變更步驟和判斷提示的順序，或是建立新的測試方法。 若要加入更多程式碼，請將游標放在測試方法上，並在捷徑功能表上選擇 [產生自動程式化 UI 測試的程式碼]。

- 將稱為 `AssertForAddTwoNumbers` 的方法加入至 UI 對應 (UIMap.uitest)。 此檔案會在自動程式化 UI 測試編輯器中開啟，而您可以在此編輯器中編輯判斷提示。

   ![使用自動程式化 UI 測試編輯器編輯判斷提示](../test/media/cuit-editor-assert.png "CUIT_Editor_assert")

   如需詳細資訊，請參閱[使用自動程式化 UI 測試編輯器來編輯自動程式化 UI 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

   您也可以檢視 UIMap.Designer.cs 中針對判斷提示方法產生的程式碼。 不過，您不應該編輯此檔案。 如果您想要建立程式碼的調整版本，請將方法複製至另一個檔案 (例如 UIMap.cs)，並重新命名方法，然後在那裏進行編輯。

  ```
  public void AssertForAddTwoNumbers()
  {
      ...
  }
  ```

  *我嘗試從 [自動程式碼 UI 測試產生器] 選取 [加入判斷提示] 工具時，想要選取的控制項失去焦點並消失。如何選取該控制項？* 
  **選取隱藏的控制項，使用鍵盤**

  有時，[加入控制項並驗證其屬性](#VerifyingCodeUsingCUITGenerateAssertions)時，您可能需要使用鍵盤。 例如，如果您嘗試錄製使用操作功能表控制項的自動程式化 UI 測試，則在嘗試從 [自動程式化 UI 測試產生器] 中選取 [加入判斷提示] 工具時，控制項中的功能表項目清單會失去焦點並消失。 這示範於下圖中，其中，如果您嘗試使用 [加入判斷提示] 工具選取 Internet Explorer 中的操作功能表，則該操作功能表會失去焦點並消失。

  ![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest-selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")

  若要使用鍵盤選取 UI 控制項，請使用滑鼠將滑鼠指標移至控制項上方。 然後同時按住 **Ctrl** 鍵和 **I** 鍵。 放開按鍵。 此控制項是透過自動程式碼 UI 測試產生器所錄製。

> [!WARNING]
>  如果您使用 Microsoft Lync，則必須先關閉 Lync，再啟動自動程式化 UI 測試產生器。 Microsoft Lync 會妨礙 **Ctrl+I** 鍵盤快速鍵。

 *我無法錄製控制項上的滑鼠停留。有什麼方法可以解決這個問題？*
 **手動錄製滑鼠停留**

 在部分情況下，正用於自動程式化 UI 測試中的特定控制項可能需要您使用鍵盤手動錄製滑鼠停留事件。 例如，當您測試 Windows Form 或 Windows Presentation Foundation (WPF) 應用程式時，可能會有自訂程式碼。 或者，可能會有針對將滑鼠指標移至控制項上方所定義的特殊行為 (例如在使用者將滑鼠指標移至樹狀節點上方時展開的樹狀節點)。 若要測試這類情況，您需要按預先定義的鍵盤按鍵，手動通知自動程式碼 UI 測試產生器：您正在將滑鼠指標移至控制項上方。

 當您執行自動程式碼 UI 測試時，請將滑鼠指標移至控制項上方。 然後，按住 Ctrl，同時按住鍵盤上的 Shift 和 R 鍵。 放開按鍵。 滑鼠停留事件是透過自動程式化 UI 測試產生器所錄製。

 ![CodedUI&#95;Hover](../test/media/codedui-hover.png "CodedUI_Hover")

 在您產生測試方法之後，會在 UIMap.Desinger.cs 檔案中加入與下列範例類似的程式碼：

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));

```

 *在我環境的其他位置中正在使用用於擷取滑鼠停留事件的按鍵指派。我可以變更預設按鍵指派嗎？*
 **設定滑鼠停留鍵盤指派**

 用來在自動程式化 UI 測試中套用滑鼠停留事件的預設鍵盤指派 Ctrl+Shift+R，視需要可以設定成使用不同的按鍵。

> [!WARNING]
>  在一般情況下，您應該不需要變更滑鼠停留事件的鍵盤指派。 重新指派鍵盤指派時請小心。 您的選擇可能已在 Visual Studio 或正在測試之應用程式的其他位置中使用。

 若要變更鍵盤指派，您必須修改下列組態檔：

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 在組態檔中，變更 `HoverKeyModifier` 和 `HoverKey` 索引鍵的值，以修改鍵盤指派：

```
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>

```

 *我在網站上錄製滑鼠停留時發生問題。這個問題有修正方法嗎？*
 **設定網頁瀏覽器的隱含滑鼠停留**

 在許多網站中，當您將滑鼠指標移至特定控制項上方時，會展開該控制項以顯示其他詳細資料。 一般而言，這些就像桌面應用程式中的功能表。 因為這是一般模式，所以自動程式碼 UI 測試會啟用進行 Web 瀏覽的隱含暫留。 例如，如果您在 Internet Explorer 中錄製暫留，則會引發事件。 這些事件可能會導致錄製多餘的暫留。 因此，會在 UI 測試組態檔中錄製隱含暫留，而且 `ContinueOnError` 設定為 `true`。 這允許在暫留事件失敗時繼續播放。

 若要啟用在網頁瀏覽器中錄製隱含暫留，請開啟組態檔：

 `<drive letter:>\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\CodedUITestBuilder.exe.config`

 確認組態檔的索引鍵 `RecordImplicitiHovers` 設定為值 `true` (如下列範例所示)：

```
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>

```

##  <a name="VerifyingCodeCUITModify"></a> 自訂您的自動程式化 UI 測試
 在您建立自動程式化 UI 測試之後，就可以在 Visual Studio 中使用下列任何工具對其進行編輯：

-   自動程式化 UI 測試產生器若要將其他控制項和驗證加入至您的測試中使用自動程式化 UI 測試產生器。 請參閱本主題中的[加入控制項並驗證其屬性](#VerifyingCodeUsingCUITGenerateAssertions)小節。

-   **自動程式化 UI 測試編輯器：** 自動程式碼 UI 測試編輯器可讓您輕鬆地修改自動程式碼 UI 測試。 您可以使用自動程式碼 UI 測試編輯器，尋找、檢視和編輯您的測試方法。 您也可以在 UI 控制項對應中編輯 UI 動作和其相關聯控制項。 如需詳細資訊，請參閱[使用自動程式化 UI 測試編輯器來編輯自動程式化 UI 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

-   **程式碼編輯器：**

    -   手動加入您測試中控制項的程式碼 (如本主題的[編寫 UI 控制項動作和屬性的程式碼](#VerifyingCodeCUITActionsandProperties)小節所述)。

    -   在您建立自動程式化 UI 測試之後，就可以將它修改為透過資料驅動。 如需詳細資訊，請參閱[建立資料驅動自動程式化 UI 測試](../test/creating-a-data-driven-coded-ui-test.md)。

    -   在自動程式化 UI 測試播放中，您可以指示測試等待發生特定事件 (例如出現視窗、進度列消失等)。 若要這樣做，請加入適當的 UITestControl.WaitForControlXXX() 方法。 如需可用方法的完整清單，請參閱[讓自動程式化 UI 測試在播放期間等候特定事件](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)。 如需等待需使用 WaitForControlEnabled 方法啟用控制項的自動程式化 UI 測試的範例，請參閱[逐步解說：建立、 編輯和維護自動程式化的 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)。

    -   自動程式化 UI 測試支援 Internet Explorer 9 和 Internet Explorer 10 所含的一些 HTML5 控制項。 如需詳細資訊，請參閱[在自動程式化 UI 測試中使用 HTML5 控制項](../test/using-html5-controls-in-coded-ui-tests.md)。

    -   **自動程式化 UI 測試編寫指導：**

        -   [自動程式化 UI 測試的結構](../test/anatomy-of-a-coded-ui-test.md)

        -   [自動程式化 UI 測試的最佳做法](../test/best-practices-for-coded-ui-tests.md)

        -   [測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)

        -   [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

###  <a name="generatedCode"></a> 產生的程式碼
 當您選擇 [產生程式碼] 時，會建立數段程式碼：

- **測試方法中的行。**

  ```csharp
  [CodedUITest]
  public class CodedUITest1
  { ...
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        // To generate more code for this test, select
        // "Generate Code" from the shortcut menu.      }
  }
  ```

   您可以在此方法上按一下滑鼠右鍵，加入更多已錄製的動作和驗證。 您也可以手動編輯它，以擴充或修改程式碼。 例如，您可以在迴圈中括住程式碼的一部分。

   您也可以加入新的測試方法，以及使用相同的方式在其中加入程式碼。 每種測試方法都必須要有 `[TestMethod]` 屬性。

- **UIMap.uitest 中的方法**

   此方法包括您所錄製的動作或所驗證值的詳細資料。 您可以開啟 UIMap.uitest 來編輯此程式碼。 它會在特殊編輯器中開啟，而您可以在其中刪除或重構所錄製動作。

   您也可以檢視 UIMap.Designer.cs 中產生的方法。 此方法會執行您在執行測試時所錄製的動作。

  ```csharp
  // File: UIMap.Designer.cs
  public partial class UIMap
  {
    /// <summary>
    /// Add two numbers
    /// </summary>
    public void AddTwoNumbers()
    { ...   }
  }
  ```

  > [!WARNING]
  >  您不應該編輯此檔案，因為它會在您建立其他測試時重新產生。

   您可以將這些方法複製至 UIMap.cs，以建立這些方法的調整版本。 例如，您可以建立可從測試方法呼叫的參數化版本：

  ```csharp
  // File: UIMap.cs
  public partial class UIMap // Same partial class
  {
    /// <summary>
    /// Add two numbers – parameterized version
    /// </summary>
    public void AddTwoNumbers(int firstNumber, int secondNumber)
    { ...   // Code modified to use parameters.
    }
  }
  ```

- **UIMap.uitest 中的宣告**

   這些宣告代表您測試所使用之應用程式的 UI 控制項。 產生的程式碼會使用它們來操作控制項以及存取其屬性。

   如果您撰寫專屬程式碼，則也可以使用它們。 例如，您可以讓測試方法選擇 Web 應用程式中的超連結、在文字方塊中輸入值，或分出分支，並根據欄位中的值採取不同的測試動作。

   您可以加入多個自動程式化 UI 測試以及多個 UI 對應物件和檔案，以促進測試大型應用程式。 如需詳細資訊，請參閱[測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)。

  如需產生的程式碼的詳細資訊，請參閱[自動程式化 UI 測試的結構](../test/anatomy-of-a-coded-ui-test.md)。

###  <a name="actions"></a> 編寫 UI 控制項動作和屬性的程式碼
 當您在自動程式化 UI 測試中使用 UI 測試控制項時，UI 測試控制項分成兩個部分：動作和屬性。

- 第一個部分包含您可以對 UI 測試控制項執行的動作。 例如，自動程式碼 UI 測試可以在 UI 測試控制項上模擬按一下滑鼠，或模擬在鍵盤上鍵入的按鍵來影響 UI 測試控制項。

- 第二個部分包含可讓您在 UI 測試控制項上取得和設定屬性。 例如，自動程式碼 UI 測試可以取得 `ListBox` 中的項目計數，或將 `CheckBox` 設定為選取的狀態。

  **存取 UI 測試控制項的動作**

  若要對 UI 測試控制項執行動作 (例如按一下滑鼠或鍵盤動作)，請在 <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> 和 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> 類別中使用方法：

- 若要執行滑鼠導向的動作 (例如按一下滑鼠)，請在 UI 測試控制項上使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>。

   `Mouse.Click(buttonCancel);`

- 若要執行滑鼠導向的動作 (例如按一下滑鼠)，請在 UI 測試控制項上使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>。

   `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

  **存取 UI 測試控制項的屬性**

  若要取得和設定 UI 控制項特定屬性值，您可以直接取得或設定控制項屬性值，也可以搭配使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> 和 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> 方法與您想要取得或設定的特定屬性名稱。

  <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> 會傳回物件，接著可以將物件轉換為適當的 <xref:System.Type>。 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> 會接受屬性值的物件。

##### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>直接從 UI 測試控制項取得或設定屬性

-   使用衍生自 T:Microsoft.VisualStudio.TestTools.UITesting.UITestControl 的控制項 (例如 T:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList 或 T:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox)，您可以直接取得或設定其屬性值，如下所示：

    ```
    int i = myHtmlList.ItemCount;
    myWinCheckBox.Checked = true;
    ```

##### <a name="to-get-properties-from-ui-test-controls"></a>從 UI 測試控制項取得屬性

-   若要從控制項取得屬性值，請使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>。

-   若要指定要取得的控制項的屬性，請將來自每個控制項中 `PropertyNames` 類別的適當字串當成 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> 的參數使用。

-   <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> 會傳回適當的資料類型，但是此傳回值會轉換為 <xref:System.Object>。 傳回 <xref:System.Object> 接著必須轉換為適當的類型。

     範例：

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

##### <a name="to-set-properties-for-ui-test-controls"></a>設定 UI 測試控制項的屬性

-   若要設定控制項中的屬性，請使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>。

-   若要指定要設定的控制項的屬性，請將來自 `PropertyNames` 類別的適當字串當成 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> 的第一個參數使用，而屬性值當成第二個參數使用。

     範例：

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

###  <a name="debugging"></a> 偵錯
 您可以使用自動程式化 UI 測試記錄來分析自動程式化 UI 測試。 自動程式碼 UI 測試記錄會篩選和錄製您自動程式碼 UI 測試執行的重要資訊。 記錄的格式可讓您快速偵錯問題。 如需詳細資訊，請參閱[使用自動程式化 UI 測試記錄分析自動程式化 UI 測試](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)。

##  <a name="VerifyCodeUsingCUITWhatsNext"></a> 後續步驟
 **其他選項來執行自動程式化 UI 測試：** 本主題稍早所述，您可以直接從 Visual Studio 中，執行自動程式化的 UI 測試。 此外，您可以從 [!INCLUDE[TCMext](../includes/tcmext-md.md)] 或 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 執行自動化 UI 測試。 與其他自動化測試不同，如果自動化自動程式化 UI 測試，則在您執行程式碼 UI 測試時，其必須與桌面進行互動。

- [如何：從 Microsoft Visual Studio 執行測試](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

- [在 Microsoft Test Manager 中執行自動化測試](http://msdn.microsoft.com/en-us/0632f265-63fe-4859-a413-9bb934c66835)

- [如何：設定和執行已排程的測試在建置您的應用程式之後](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)

- [在建置流程中執行測試](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)

- [從命令列執行自動化測試](http://msdn.microsoft.com/library/f18179c6-b688-4e41-9898-8aca130c4fc3)

- [如何：若要執行與桌面互動的測試設定測試代理程式](/visualstudio/test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop?view=vs-2015)

- [&#91;已停用&#93;在負載測試中使用自動程式化 UI 測試](http://msdn.microsoft.com/library/704339ff-7da7-4d5f-acb3-c3b23f4acb43)

  **加入自訂控制項的支援：** 自動程式化的 UI 測試架構不支援每個可能的 UI，而且可能不支援您想要測試的 UI。 例如，您無法立即為 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 的 UI 建立自動程式碼 UI 測試。 不過，您可以建立自動程式化 UI 測試架構的擴充功能，以支援自訂控制項。

- [啟用控制項的自動程式化 UI 測試](../test/enable-coded-ui-testing-of-your-controls.md)

- [擴充自動程式化 UI 測試和動作記錄以支援 Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

  自動程式化 UI 測試經常用來自動化手動測試。 如需其他指引，請參閱[Testing for Continuous Delivery with Visual Studio 2012 – 第 5 章：自動化系統測試](http://go.microsoft.com/fwlink/?LinkID=255196)。 如需手動測試的詳細資訊，請參閱[&#91;已停用&#93;使用 Microsoft Test Manager 建立手動測試案例](http://msdn.microsoft.com/library/9989e184-c8e4-444b-998d-a1a5ec94461e)。 如需自動化系統測試的詳細資訊，請參閱[使用 Microsoft Test Manager 建立自動化測試](http://msdn.microsoft.com/en-us/7b5075ee-ddfe-411d-b1d4-94283550a5d0)。

## <a name="external-resources"></a>外部資源

### <a name="guidance"></a>指導方針
- [測試 for Continuous Delivery with Visual Studio 2012 – 第 2 章：單元測試測試內部](http://go.microsoft.com/fwlink/?LinkID=255188)

- [測試 for Continuous Delivery with Visual Studio 2012 – Chapter 5:自動化系統測試](http://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="faq"></a>常見問題集
- [自動程式碼 UI 測試常見問題集 - 1](http://go.microsoft.com/fwlink/?LinkID=230576)

- [自動程式碼 UI 測試常見問題集 - 2](http://go.microsoft.com/fwlink/?LinkID=230578)

### <a name="forum"></a>論壇
- [Visual Studio 使用者介面自動化測試 (包括 CodedUI)](http://go.microsoft.com/fwlink/?LinkID=224497)

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [改善程式碼品質](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)
- [逐步解說：建立、 編輯和維護自動程式化的 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [自動程式化 UI 測試的結構](../test/anatomy-of-a-coded-ui-test.md)
- [自動程式化 UI 測試的最佳做法](../test/best-practices-for-coded-ui-tests.md)
- [測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [使用自動程式化 UI 測試編輯器來編輯自動程式化 UI 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [升級 Visual Studio 2010 的自動程式化 UI 測試](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
- [從現有的動作記錄產生自動程式碼 UI 測試](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
