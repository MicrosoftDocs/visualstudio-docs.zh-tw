---
title: 自動程式化 UI 測試
description: 瞭解如何在 [自動程式碼 UI 測試產生器] 于背景執行時，手動執行測試，以在 Visual Studio 中建立自動程式化 UI 測試。
ms.custom: SEO-VS-2020
ms.date: 12/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3da0a3868b410fbb78ed98265eb8f0920e6482b
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330104"
---
# <a name="use-coded-ui-test-to-test-your-code"></a>使用自動程式化 UI 測試來測試您的程式碼

自動程式化 UI 測試 (CUIT) 可透過使用者介面 (UI) 推動您的應用程式。 這些測試包括 UI 控制項的功能測試。 它們可讓您確認整個應用程式 (包括其使用者介面) 正確運作。 自動程式化 UI 測試適用於使用者介面中有驗證或其他邏輯時 (例如，在網頁中)。 它們也經常用來自動化現有手動測試。

在 Visual Studio 中建立自動程式化 UI 測試十分簡單。 您只需在「自動程式化 UI 測試產生器」於背景執行時，手動執行測試即可。 您也可以指定特定欄位中應該出現的值。 「自動程式化 UI 測試產生器」會錄製您的動作，然後從這些動作產生程式碼。 建立測試之後，即可使用特殊編輯器來編輯該測試，以讓您修改動作的順序。

即使您的主要技能是測試而非撰寫程式碼，特製化 **自動程式化 UI 測試產生器** 和編輯器也可讓您輕鬆建立和編輯自動程式化 UI 測試。 但是，如果您是開發人員，而且想要使用更進階的方式擴充測試，請讓程式碼更具結構性，以直接複製和調整。 例如，您可能錄製一個在網站上購買某項東西的測試，接著編輯產生的程式碼以加入購買許多項目的迴圈。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="requirements"></a>規格需求

- Visual Studio Enterprise
- 自動程式化 UI 測試元件

如需自動程式碼 UI 測試支援哪些平臺和設定的詳細資訊，請參閱 [支援的平臺](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)。

## <a name="install-the-coded-ui-test-component"></a>安裝自動程式化 UI 測試元件

若要存取自動程式化 UI 測試工具和範本，請安裝 Visual Studio 的 **自動程式化 UI 測試** 元件。

1. 選擇 [工具] > [取得工具和功能] 以啟動 **Visual Studio 安裝程式**。

1. 在 **Visual Studio 安裝程式** 中，選擇 [個別元件] 索引標籤，然後向下捲動至 [偵錯和測試] 區段。 選取 [自動程式化 UI 測試] 元件。

   ![自動程式化 UI 測試元件](media/coded-ui-test-component.png)

1. 選取 [修改]。

## <a name="create-a-coded-ui-test"></a>建立自動程式化 UI 測試

1. 建立自動程式化 UI 測試專案。

   自動程式化 UI 測試必須包含在自動程式化 UI 測試專案中。 如果您還沒有自動程式化 UI 測試專案，請予以建立。 選擇 **[** 檔案  >  **新增**  >  **專案**]。 搜尋並選取 [自動程式化 UI 測試專案] 專案範本。

   ::: moniker range="vs-2017"

   ![[新增專案] 對話方塊中的 [自動程式化 UI 測試專案] 範本](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > 如果您沒有看到 [自動程式化 UI 測試專案] 範本，則需要[安裝自動程式化 UI 測試元件](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)。

2. 新增自動程式化 UI 測試檔案。

     如果您剛剛建立自動程式碼 UI 專案，則自動加入第一個 CUIT 檔案。 若要加入另一個測試檔案，請在 **方案總管** 中開啟自動程式碼 ui 測試專案的快捷方式功能表，然後選擇 [**加入** 自動程式化  >  **ui 測試**]。

     在 [產生自動程式化 UI 測試的程式碼] 對話方塊中，選擇 [錄製動作] > [編輯 UI 對應或加入判斷提示]。

     ![[產生自動程式化 UI 測試的程式碼] 對話方塊](media/generate-code-for-coded-ui-test.png)

     自動程式 **代碼 UI 測試** 產生器隨即出現。

     ![自動程式碼 UI 測試產生器](../test/media/codedui_testbuilder.png)

3. 錄製一連串的動作。

     **若要開始錄製**，請選擇 [錄製] 圖示。 執行您想要在應用程式中測試的動作 (包括在必要時啟動應用程式)。 例如，如果您是測試 Web 應用程式，則可能會啟動瀏覽器、巡覽到網站，然後登入應用程式。

     **若要暫停錄製** (例如，如果您需要處理傳入的電子郵件)，請選擇 [暫停]。

    > [!WARNING]
    > 將會錄製所有在桌面上執行的動作。 如果您執行的動作可能會導致在錄製中包括敏感性資料，則請暫停錄製。

     **若要刪除錯誤錄製的動作**，請選擇 [編輯步驟]。

     **若要產生** 會複寫動作的程式碼，請選擇 [ **產生程式碼** ] 圖示，並輸入自動程式化 UI 測試方法的名稱和描述。

4. 確認 UI 欄位 (例如文字方塊) 中的值。

     選擇 [自動程式 **代碼 UI 測試** 產生器] 中的 [**加入判斷** 提示]，然後在執行中的應用程式中選擇 UI 控制項。 在顯示的屬性清單中選取屬性，例如，文字方塊中的 [文字]。 在捷徑功能表上，選擇 [加入判斷提示]。 在此對話方塊中，選取比較運算子、比較值和錯誤訊息。

     關閉判斷提示視窗，然後選擇 [產生程式碼]。

     ![自動程式碼 UI 測試目標項目](../test/media/codedui_1.png)

    > [!TIP]
    > 在錄製動作與確認值之間替換。 在每串動作或驗證結束時產生程式碼。 如果您想要，則可以稍後插入新的動作和驗證。

     如需詳細資料，請參閱[驗證控制項屬性](#validate-the-properties-of-ui-controls)。

5. 檢視產生的測試程式碼。

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

6. 新增其他動作和判斷提示。

   將游標放在測試方法中的適當點，然後在捷徑功能表上選擇 [產生自動程式化 UI 測試的程式碼]。 將會在該點插入新的程式碼。

7. 編輯測試動作和判斷提示的詳細資料。

     開啟 *UIMap. uitest*。 這個檔案會在 [自動程式化 **UI 測試編輯器**] 中開啟，您可以在其中編輯所記錄的任何動作順序，以及編輯您的判斷提示。

     ![自動程式碼 UI 測試編輯器](../test/media/cuit_editor_edit.png)

     如需詳細資訊，請參閱使用自動程式 [代碼 Ui 測試編輯器來編輯自動程式碼 ui 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

8. 執行測試。

   使用 [測試總管]，或開啟測試方法中的捷徑功能表，然後選擇 [執行測試]。 如需如何執行測試的詳細資訊，請參閱本主題結尾的「[下一步](#whats-next)」一節中的 [使用 Test Explorer 執行單元測試](../test/run-unit-tests-with-test-explorer.md)，以及執行自動 *程式碼 UI 測試的其他選項*。

本主題中的其餘各節提供此程序中各步驟的更多詳細資料。

如需更詳細的範例，請參閱 [逐步解說：建立、編輯和維護自動程式碼 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)。 在這個逐步解說中，您將建立簡單的 Windows Presentation Foundation (WPF) 應用程式，以示範如何建立、編輯和維護自動程式化 UI 測試。 本逐步解說提供解決方案用來修正各種因時間問題和控制項重構而中斷的測試。

## <a name="start-and-stop-the-application-under-test"></a>啟動和停止受測試的應用程式

如果您不想要分別針對每個測試啟動和停止應用程式、瀏覽器或資料庫，請執行下列其中一項動作：

- 如果您不想要錄製可啟動待測應用程式的動作，則必須先啟動應用程式，再選擇 **錄製** 圖示。

- 在測試結束時，會終止在其中執行測試的流程。 如果您已在測試中啟動應用程式，則通常會關閉該應用程式。  如果您不想要測試在結束時關閉應用程式，請將 *.runsettings* 檔案新增至解決方案，並使用 `KeepExecutorAliveAfterLegacyRun` 選項。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

- 新增測試初始化方法 (透過 `[TestInitialize]` 屬性予以識別)，此方法會在每個測試方法開始時執行程式碼。 例如，您可以從 TestInitialize 方法啟動應用程式。

- 新增測試清除方法 (透過 `[TestCleanup]` 屬性予以識別)，此方法會在每個測試方法結束時執行程式碼。 例如，可以從 TestCleanup 方法呼叫關閉應用程式的方法。

## <a name="validate-the-properties-of-ui-controls"></a>驗證 UI 控制項的屬性

您可以使用 [自動程式化 UI 測試產生器] 將使用者介面 (UI) 控制項加入 [UIMap](/previous-versions/dd580454(v=vs.140)) 以進行測試，或產生可使用 UI 控制項判斷提示之驗證方法的程式碼。

若要產生 UI 控制項的判斷提示，請選擇自動程式化 **Ui 測試** 產生器中的 [**加入判斷** 提示] 工具，並將它拖曳至待測應用程式上的控制項，您想要驗證是否正確。 有方塊括住控制項時，請放開滑鼠。 此控制類別程式碼會立即在 *UIMap.Designer.cs* 檔案中建立。

![自動程式碼 UI 測試目標項目](../test/media/codedui_1.png)

此控制項的屬性現在會列在 [加入判斷提示] 對話方塊中。

另一種巡覽至特定控制項的方式，是選擇箭號 **(<<)** 展開 [UI 控制項對應] 的檢視。 若要尋找父控制項、同層級控制項或子控制項，您可以按一下對應中的任何位置，並使用方向鍵在樹狀目錄中移動。

![自動程式碼 UI 測試屬性](../test/media/codedui_2.png)

> [!TIP]
> 如果在應用程式中選取控制項時沒有看到任何屬性，或是在 UI 控制項對應中沒有看到控制項，請確認控制項在應用程式程式碼中有唯一的識別碼。 唯一識別碼可以是 HTML ID 屬性或 WPF UId。

接下來，開啟想要驗證之 UI 控制項的屬性的捷徑功能表，然後指向 [加入判斷提示]。 在 [新增判斷提示] 對話方塊中，選取您判斷提示的 [比較子] (例如 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>)，然後在 [比較值] 中輸入您判斷提示的值。

![自動程式碼 UI 測試判斷提示](../test/media/codedui_3.png)

加入您測試的所有判斷提示之後，請選擇 [確定]。

若要產生您判斷提示的程式碼，並將控制項加入至 UI 對應，請選擇 [產生程式碼] 圖示。 鍵入您的自動程式化 UI 測試方法名稱，以及該方法的描述，這些將會新增為該方法的註解。 選擇 [加入並產生]。 接下來，選擇 [關閉] 圖示關閉 [自動程式化 UI 測試產生器]。 這樣會產生與下列程式碼類似的程式碼。 例如，如果您輸入的名稱是 `AssertForAddTwoNumbers`，則程式碼會與此範例類似：

- 將判斷提示方法 AssertForAddTwoNumbers 呼叫新增至您自動程式化 UI 測試檔案中的測試方法：

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     您可以編輯此檔案以變更步驟和判斷提示的順序，或是建立新的測試方法。 若要加入更多程式碼，請將游標放在測試方法上，並在捷徑功能表上選擇 [產生自動程式化 UI 測試的程式碼]。

- 將呼叫的方法加入 `AssertForAddTwoNumbers` 至 UI 對應， (*UIMap uitest*) 。 這個檔案會在 [自動程式 **代碼 UI 測試編輯器**] 中開啟，您可以在其中編輯判斷提示。

     ![使用自動程式化 UI 測試編輯器編輯判斷提示](../test/media/cuit_editor_assert.png)

     如需詳細資訊，請參閱使用自動程式 [代碼 ui 測試編輯器來編輯自動程式碼 ui 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

     您也可以在 *UIMap.Designer.cs* 中查看判斷提示方法的產生程式碼。 不過，您不應該編輯此檔案。 如果您想要建立程式碼的調整版本，請將方法複製到另一個檔案，例如 *UIMap.cs*、重新命名方法，然後在該處進行編輯。

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>使用鍵盤選取隱藏控制項

如果您從 [自動程式碼 UI 測試產生器] 中選取 [加入判斷提示] 工具時，想要選取的控制項失去焦點並消失：

有時，新增控制項並驗證其屬性時，您可能需要使用鍵盤。 例如，如果您嘗試錄製使用右鍵功能表控制項的自動程式化 UI 測試，則在嘗試從 [自動程式化 UI 測試產生器] 中選取 [新增判斷提示] 工具時，控制項中的功能表項目清單將會失去焦點並消失。 下圖示範了這一點，如果您嘗試使用 [加入判斷提示] 工具選取 Internet Explorer 中的右鍵功能表，則該右鍵功能表會失去焦點並消失。

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png)

若要使用鍵盤選取 UI 控制項，請使用滑鼠將滑鼠指標移至控制項上方。 然後同時按住 **Ctrl** 鍵和 **I** 鍵。 放開按鍵。 此控制項是透過 [自動程式碼 UI 測試產生器] 所錄製。

#### <a name="manually-record-mouse-hovers"></a>手動錄製滑鼠停留

如果您無法錄製控制項上的滑鼠停留：

在部分情況下，正用於自動程式化 UI 測試中的特定控制項可能需要您使用鍵盤手動錄製滑鼠停留事件。 例如，當您測試 Windows Form 或 Windows Presentation Foundation (WPF) 應用程式時，可能會有自訂程式碼。 或者，可能會有針對將滑鼠指標移至控制項上方所定義的特殊行為 (例如在使用者將滑鼠指標移至樹狀節點上方時展開的樹狀節點)。 若要測試這類情況，您必須按預先定義的鍵盤按鍵，手動通知自動程式 **代碼 UI 測試** 產生器。

當您執行自動程式化 UI 測試時，請將滑鼠指標移至控制項上方。 然後按住 **Ctrl** 鍵，同時按住鍵盤上的 **Shift** 和 **R** 鍵。 放開按鍵。 滑鼠停留事件是透過 [自動程式化 UI 測試產生器] 所錄製。

![CodedUI&#95;Hover](../test/media/codedui_hover.png)

在您產生測試方法之後，會在 *UIMap.Designer.cs* 檔案中加入與下列範例類似的程式碼：

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>設定滑鼠停留鍵盤指派

如果在我環境的其他位置中正在使用用於擷取滑鼠停留事件的按鍵指派：

如有必要， **Ctrl** + **Shift** + 您可以將用來在自動程式化 UI 測試中套用滑鼠停留事件的預設鍵盤指派（Ctrl Shift **R** ）設定為使用不同的索引鍵。

> [!WARNING]
> 在一般情況下，您應該不需要變更滑鼠停留事件的鍵盤指派。 重新指派鍵盤指派時請小心。 您的選擇可能已在 Visual Studio 或正在測試之應用程式的其他位置中使用。

若要變更鍵盤指派，請修改下列設定檔：

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

在組態檔中，變更 `HoverKeyModifier` 和 `HoverKey` 索引鍵的值，以修改鍵盤指派：

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>設定網頁瀏覽器的隱含滑鼠停留

如果您在網站上錄製滑鼠停留時發生問題：

在許多網站中，當您將滑鼠指標移至特定控制項上方時，會展開該控制項以顯示其他詳細資料。 一般而言，這些就像桌面應用程式中的功能表。 因為這是一般模式，所以自動程式化 UI 測試會啟用進行網頁瀏覽的隱含暫留。 例如，如果您在 Internet Explorer 中錄製暫留，則會引發事件。 這些事件可能會導致錄製多餘的暫留。 因此，會在 UI 測試組態檔中錄製隱含暫留，而且 `ContinueOnError` 設定為 `true`。 這允許在暫留事件失敗時繼續播放。

若要啟用在網頁瀏覽器中錄製隱含暫留，請開啟組態檔：

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

確認組態檔的索引鍵 `RecordImplicitiHovers` 已設定為值 `true` (如下列範例所示)：

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>自訂自動程式化 UI 測試

在您建立自動程式化 UI 測試之後，就可以在 Visual Studio 中使用下列任何工具對其進行編輯：

- 使用「自動程式化 UI 測試產生器」為測試新增額外控制項和驗證。 請參閱本主題中的[加入控制項並驗證其屬性](#validate-the-properties-of-ui-controls)一節。

- 自動程式 **代碼 Ui 測試編輯器** 可讓您輕鬆地修改自動程式化 ui 測試。 使用「自動程式化 UI 測試編輯器」時，您可以尋找、檢視及編輯測試方法。 您也可以在 UI 控制項對應中編輯 UI 動作和其相關聯控制項。 如需詳細資訊，請參閱使用自動程式 [代碼 ui 測試編輯器來編輯自動程式碼 ui 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)。

- **程式碼編輯器：**

  - 手動加入您測試中控制項的程式碼 (如本主題中的[自動程式化 UI 控制項動作和屬性](#coded-ui-control-actions-and-properties)一節所述)。

  - 在您建立自動程式化 UI 測試之後，就可以將其修改為透過資料驅動。 如需詳細資訊，請參閱 [建立資料驅動型自動程式碼 UI 測試](../test/creating-a-data-driven-coded-ui-test.md)。

  - 在自動程式化 UI 測試播放中，您可以指示測試等待發生特定事件 (例如出現視窗、進度列消失等)。 若要這樣做，請加入適當的 UITestControl.WaitForControlXXX() 方法。 如需可用方法的完整清單，請參閱[讓自動程式化 UI 測試在播放期間等候特定事件](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)。 如需使用 WaitForControlEnabled 方法等候啟用控制項的自動程式碼 UI 測試範例，請參閱 [逐步解說：建立、編輯和維護](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)自動程式化 ui 測試。

  - 自動程式化 UI 測試支援 Internet Explorer 9 和 Internet Explorer 10 所含的一些 HTML5 控制項。 如需詳細資訊，請參閱在自動程式 [代碼 UI 測試中使用 HTML5 控制項](../test/using-html5-controls-in-coded-ui-tests.md)。

  - 自動程式碼 UI 測試編寫指導：

    - [自動程式碼 UI 測試的剖析](../test/anatomy-of-a-coded-ui-test.md)

    - [自動程式碼 UI 測試的最佳作法](../test/best-practices-for-coded-ui-tests.md)

    - [使用多個 UI 對應來測試大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)

    - [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>產生的程式碼

當您選擇 [產生程式碼] 時，會建立數段程式碼：

- 測試方法中的行。

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

- *UIMap. uitest* 中的方法。

     此方法包括您所錄製的動作或所驗證值的詳細資料。 您可以藉由開啟 *UIMap uitest* 來編輯此程式碼。 它會在特殊編輯器中開啟，而您可以在其中刪除或重構所錄製動作。

     您也可以檢視 *UIMap.Designer.cs* 中產生的方法。 此方法會執行您在執行測試時所錄製的動作。

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
    > 您不應該編輯此檔案，因為它會在您建立其他測試時重新產生。

     您可以將這些方法複製至 *UIMap.cs*，以建立這些方法的調整版本。 例如，您可以建立可從測試方法呼叫的參數化版本：

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- *UIMap. uitest* 中的宣告。

    這些宣告代表您測試所使用之應用程式的 UI 控制項。 產生的程式碼會使用它們來操作控制項以及存取其屬性。

    如果您撰寫專屬程式碼，則也可以使用它們。 例如，您可以讓測試方法選擇 Web 應用程式中的超連結、在文字方塊中輸入值，或分出分支，並根據欄位中的值採取不同的測試動作。

    您可以新增多個自動程式化 UI 測試以及多個 UI 對應物件和檔案，以利於測試大型應用程式。 如需詳細資訊，請參閱[測試含有多個 UI 對應的大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)。

如需產生之程式碼的詳細資訊，請參閱自動程式化 [UI 測試的剖析](../test/anatomy-of-a-coded-ui-test.md)。

## <a name="coded-ui-control-actions-and-properties"></a>自動程式化 UI 控制項動作和屬性

當您在自動程式化 UI 測試中使用 UI 測試控制項時，UI 測試控制項分成兩個部分：動作和屬性。

- 第一個部分包含您可以對 UI 測試控制項執行的動作。 例如，自動程式化 UI 測試可以在 UI 測試控制項上模擬按一下滑鼠，或模擬在鍵盤上鍵入的按鍵來影響 UI 測試控制項。

- 第二個部分包含可讓您在 UI 測試控制項上取得和設定屬性。 例如，自動程式化 UI 測試可以取得 `ListBox` 中的項目計數，或將 `CheckBox` 設定為選取的狀態。

**存取 UI 測試控制項的動作**

若要對 UI 測試控制項執行動作 (例如按一下滑鼠或鍵盤動作)，請在 <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> 和 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> 類別中使用方法：

- 若要執行滑鼠導向的動作 (例如按一下滑鼠)，請在 UI 測試控制項上使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>。

     `Mouse.Click(buttonCancel);`

- 若要執行滑鼠導向的動作 (例如按一下滑鼠)，請在 UI 測試控制項上使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>。

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**存取 UI 測試控制項的屬性**

若要取得和設定 UI 控制項特定屬性值，您可以直接取得或設定控制項屬性值，也可以搭配使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> 和 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> 方法與您想要取得或設定的特定屬性名稱。

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> 會傳回物件，接著可以將物件轉換為適當的 <xref:System.Type>。 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> 會接受屬性值的物件。

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>直接從 UI 測試控制項取得或設定屬性

您可以使用衍生自 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> 的控制項 (例如 [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) 或 [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox))，直接取得或設定其屬性值。 下列程式碼提供了一些範例：

```csharp
int i = myHtmlList.ItemCount;
myWinCheckBox.Checked = true;
```

### <a name="to-get-properties-from-ui-test-controls"></a>從 UI 測試控制項取得屬性

- 若要從控制項取得屬性值，請使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>。

- 若要指定要取得的控制項的屬性，請將來自每個控制項中 `PropertyNames` 類別的適當字串當成 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> 的參數使用。

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> 會傳回適當的資料類型，但是此傳回值會轉換為 <xref:System.Object>。 傳回 <xref:System.Object> 接著必須轉換為適當的類型。

     範例：

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>設定 UI 測試控制項的屬性

- 若要設定控制項中的屬性，請使用 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>。

- 若要指定要設定的控制項的屬性，請將來自 `PropertyNames` 類別的適當字串當成 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> 的第一個參數使用，而屬性值當成第二個參數使用。

     範例：

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>偵錯

您可以使用自動程式化 UI 測試記錄來分析自動程式化 UI 測試。 自動程式化 UI 測試記錄會篩選並錄製您自動程式化 UI 測試回合的重要資訊。 記錄的格式可讓您快速偵錯問題。 如需詳細資訊，請參閱[使用自動程式化 UI 測試記錄分析自動程式化 UI 測試](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md)。

## <a name="whats-next"></a>接下來要做什麼？

::: moniker range="vs-2017"
**執行自動程式碼 UI 測試的其他選項：** 您可以直接從 Visual Studio 執行自動程式碼 UI 測試，如本主題稍早所述。 此外，您可以從 Microsoft Test Manager 或使用 Azure Pipelines 來執行自動化 UI 測試。 與其他自動化測試不同，如果將自動程式化 UI 測試自動化，則在您執行自動程式化 UI 測試時，其必須與桌面進行互動。
::: moniker-end
::: moniker range=">=vs-2019"
**執行自動程式碼 UI 測試的其他選項：** 您可以直接從 Visual Studio 執行自動程式碼 UI 測試，如本主題稍早所述。 此外，您也可以使用 Azure Pipelines 來執行自動化 UI 測試。 與其他自動化測試不同，如果將自動程式化 UI 測試自動化，則在您執行自動程式化 UI 測試時，其必須與桌面進行互動。
::: moniker-end

- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)

- [在建置流程中執行測試](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)

- [如何：將您的測試代理程式設定為執行與桌面互動的測試](/previous-versions/ee291332(v=vs.140))

**新增自訂控制項的支援：**  自動程式碼 UI 測試架構不支援每個可能的 UI，而且可能不支援您要測試的 UI。 例如，您無法立即為 Microsoft Excel 的 UI 建立自動程式化 UI 測試。 不過，您可以建立自動程式化 UI 測試架構的延伸模組，以支援自訂控制項。

- [啟用控制項的自動程式碼 UI 測試](../test/enable-coded-ui-testing-of-your-controls.md)

- [擴充自動程式化 UI 測試和動作記錄](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

自動程式化 UI 測試經常用於將手動測試自動化。 如需自動化測試的詳細資訊，請參閱 [Visual Studio 中的測試工具](../test/improve-code-quality.md)。

## <a name="see-also"></a>另請參閱

- [記錄和播放手動測試](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts&preserve-view=true)
- [Xamarin.UITest](/appcenter/test-cloud/uitest/)
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [逐步解說：建立、編輯和維護自動程式碼 UI 測試](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [建立自動程式碼 UI 測試來測試 UWP 應用程式](test-uwp-app-with-coded-ui-test.md)
- [自動程式碼 UI 測試的剖析](../test/anatomy-of-a-coded-ui-test.md)
- [自動程式碼 UI 測試的最佳作法](../test/best-practices-for-coded-ui-tests.md)
- [使用多個 UI 對應來測試大型應用程式](../test/testing-a-large-application-with-multiple-ui-maps.md)