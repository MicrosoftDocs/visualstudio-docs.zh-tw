---
title: 建立自動程式化 UI 測試
description: 瞭解如何使用 Windows Presentation Framework 應用程式的自動程式碼 UI 測試，並查看有時間問題和控制項重構的測試解決方案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b2c14869fa8e4a14a209f8fe5ad440d3ae0e569b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967952"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>逐步解說：建立、編輯和維護自動程式化 UI 測試

在本逐步解說中，您將了解如何建立、編輯和維護自動程式化 UI 測試來測試 Windows Presentation Framework (WPF) 應用程式。 本逐步解說提供解決方案用來修正各種因時間問題和控制項重構而中斷的測試。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>建立 WPF 應用程式

1. 建立新 **WPF 應用程式 (.NET Framework)** 專案，並命名為 **SimpleWPFApp**。

     **WPF 設計工具** 隨即開啟，並顯示專案的MainWindow。

2. 如果目前未開啟工具箱，請開啟它。 選擇 [檢視] 功能表，然後選擇 [工具箱]。

3. 在 [所有 WPF 控制項] 區段底下，將 [Button]、[CheckBox] 和 [ProgressBar] 控制項拖曳至設計介面中的 [MainWindow]。

4. 選取 [Button] 控制項。 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性的值從變更 \<No Name> 為 button1。 然後將 [Content] 屬性的值從 Button 變更為 Start。

5. 選取 [ProgressBar] 控制項。 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性的值從變更 \<No Name> 為 progressBar1。 然後將 [Maximum] 屬性的值從 **100** 變更為 **10000**。

6. 選取 [Checkbox] 控制項。 在 [ **屬性** ] 視窗中，將 [ **名稱** ] 屬性的值從變更 \<No Name> 為 checkBox1，並清除 **IsEnabled** 屬性。

     ![簡單 WPF 應用程式](../test/media/codedui_wpfapp.png)

7. 按兩下按鈕控制項以加入 Click 事件處理常式。

     *MainWindow.xmal.cs* 會顯示在 [程式碼編輯器] 中，而且游標位於新的 button1_Click 方法。

8. 在 MainWindow 類別的頂端，加入一個委派。 這個委派將用於進度列。 若要加入委派，請加入下列程式碼：

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

9. 在 button1_Click 方法中，加入下列程式碼：

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

10. 儲存檔案。

### <a name="run-the-wpf-app"></a>執行 WPF 應用程式

1. 在 [偵錯] 功能表上，選取 [開始偵錯] 或按 **F5**。

2. 請注意，會停用核取方塊控制項。 選擇 [開始]。

     進度列幾分鐘後應該 100% 完成。

3. 您現在可以選取核取方塊控制項。

4. 關閉 SimpleWPFApp。

## <a name="create-a-shortcut-to-the-wpf-app"></a>建立 WPF 應用程式的捷徑

1. 找出先前建立的 SimpleWPFApp 應用程式。

2. 建立 SimpleWPFApp 應用程式的桌面捷徑。 以滑鼠右鍵按一下 *SimpleWPFApp.exe* ，然後選擇 [ **複製**]。 在桌面上按一下滑鼠右鍵，然後選取 [貼上捷徑]。

    > [!TIP]
    > 使用應用程式的捷徑可以輕鬆新增或修改應用程式的自動程式化 UI 測試，因為它能讓您快速啟動應用程式。

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>為 SimpleWPFApp 建立自動程式化 UI 測試

1. 在 [方案總管] 中，以滑鼠右鍵按一下方案，然後選擇 [新增] > [新增專案]。

2. 搜尋並選取 [自動程式化 UI 測試專案] 專案範本，且繼續執行步驟直到專案建立完成。

   > [!NOTE]
   > 如果您沒有看到 [自動程式化 **Ui 測試專案** ] 範本，則需要安裝自動程式化 [ui 測試元件](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)。

     名為 **CodedUITestProject1** 的新自動程式化 UI 測試專案會新增至方案，且 [產生自動程式化 UI 測試的程式碼] 對話方塊會隨即出現。

1. 選取 [錄製動作、編輯 UI 對應或加入判斷提示] 選項，然後選擇 [確定]。

     [UIMap - 自動程式化 UI 測試產生器] 對話方塊隨即顯示，並將 Visual Studio 視窗最小化。

     如需對話方塊選項的詳細資訊，請參閱[建立自動程式化 UI 測試](../test/use-ui-automation-to-test-your-code.md)。

1. 在 [UIMap - 自動程式化 UI 測試產生器] 對話方塊上，選擇 [開始錄製]。

     ![開始錄製](../test/media/cuit_builder_record.png)

     您可以視需要暫停錄製 (例如，如果您需要處理傳入的電子郵件)。

     ![暫停錄製](../test/media/cuit_.png)

    > [!WARNING]
    > 將會錄製所有在桌面上執行的動作。 如果您執行的動作可能會導致在錄製中包括敏感性資料，則請暫停錄製。

1. 使用桌面捷徑啟動 SimpleWPFApp。

     和前面一樣，請注意，會停用核取方塊控制項。

1. 選擇 SimpleWPFApp 上的 [開始]。

     進度列幾分鐘後應該 100% 完成。

1. 核取現在已啟用的核取方塊控制項。

1. 關閉 SimpleWPFApp 應用程式。

1. 在 [UIMap - 自動程式化 UI 測試產生器] 對話方塊上，選擇 [產生程式碼]。

1. 在 [方法名稱] 方塊中鍵入 **SimpleAppTest**，然後選擇 [新增和產生]。 自動程式化 UI 測試幾分鐘後會出現並新增至方案。

1. 關閉 **UIMap 自動程式碼 UI 測試** 產生器。

     *CodedUITest1.cs* 檔會出現在程式碼編輯器中。

1. 儲存您的專案。

### <a name="run-the-test"></a>執行測試

1. 從 [測試] 功能表中，選擇 [Windows]，然後選擇 [測試總管]。

2. 從 [ **組建** ] 功能表中，選擇 [ **建立方案**]。

3. 在 *CodedUITest1.cs* 檔案中，找出 [ **CodedUITestMethod** ] 方法，按一下滑鼠右鍵並選取 [ **執行測試**]，或從 **test Explorer** 執行測試。

   當自動程式化 UI 測試執行時，會顯示 SimpleWPFApp。 它會處理您在先前程序執行的步驟。 不過，當測試嘗試選取核取方塊控制項的核取方塊時， **測試結果** 視窗會顯示測試失敗。 這是因為這個測試嘗試選取核取方塊，但是一直到在進度列 100% 完成之後才發現核取方塊控制項已停用。 您可以使用各種可供自動程式碼 UI 測試使用的 `UITestControl.WaitForControlXXX()` 方法，來修正這個 (或類似) 問題。 下一個程序將示範使用 `WaitForControlEnabled()` 方法來修正導致這個測試失敗的問題。 如需詳細資訊，請參閱[讓自動程式化 UI 測試在播放期間等候特定事件](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)。

## <a name="edit-and-rerun-the-coded-ui-test"></a>編輯和重新執行自動程式化 UI 測試

1. 在 [ **測試瀏覽器** ] 視窗中，選取失敗的測試，然後在 [ **StackTrace** ] 區段中，選擇第一個指向 **UIMap. SimpleAppTest ( # B1** 的連結。

2. *UIMap.Designer.cs* 檔案隨即開啟，並在程式碼中反白顯示錯誤點：

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. 若要修正這個問題，您可以使用 `WaitForControlEnabled()` 方法，讓自動程式碼 UI 測試先等候 [CheckBox] 控制項完成啟用後再繼續進行至這一行。

    > [!WARNING]
    > 請勿修改 *UIMap.Designer.cs* 檔。 每次您使用 [UIMap - 自動程式化 UI 測試產生器] 產生程式碼時，您所做的任何程式碼變更都會被覆寫。 如果您需要修改錄製的方法，請將它複製到 *UIMap.cs* 檔案並重新命名。 *UIMap.cs* 檔案可用來覆寫 *UIMapDesigner.cs* 檔案中的方法和屬性。 您必須移除 *CodedUITest.cs* 檔案中原始方法的參考，並將它取代為重新命名的方法名稱。

4. 在 **方案總管** 中，找出自動程式碼 UI 測試專案中的 *UIMap. uitest* 。

5. 開啟 *UIMap.uitest* 的捷徑功能表，並選擇 [開啟]。

     此自動程式碼 UI 測試隨即在 [自動程式碼 UI 測試編輯器] 中顯示。 您現在可以檢視及編輯自動程式化 UI 測試。

6. 在 [UI 動作] 窗格中，選取您要移至 *UIMap.cs* 或 *UIMap.vb* 檔案的測試方法 (SimpleAppTest)。 將此方法移至不同的檔案即可新增自訂程式碼，重新編譯測試程式碼時不會覆寫此程式碼。

7. 選擇 [自動程式碼 **UI 測試編輯器**] 工具列上的 [**移動程式碼**] 按鈕。

8. Microsoft Visual Studio 對話方塊隨即顯示。 它會警告此方法將從 *UIMap.uitest* 檔案移至 *UIMap.cs* 檔案，而且您將無法再使用 [自動程式化 UI 測試編輯器] 編輯此方法。 選擇 [ **是**]。

     測試方法會從 *UIMap.uitest* 檔案移除，不再顯示在 [UI 動作] 窗格中。 若要編輯移動的測試檔案，請從 **方案總管** 開啟 *UIMap.cs* 檔案。

9. 在 Visual Studio 工具列上，選擇 [儲存]。

     測試方法的更新會儲存在 *UIMap* 檔中。

    > [!WARNING]
    > 一旦移動方法，便無法使用 [自動程式碼 UI 測試編輯器] 來編輯方法。 您必須使用 [程式碼編輯器] 加入及維護自訂程式碼。

10. 將這個方法從 `SimpleAppTest()` 重新命名為 `ModifiedSimpleAppTest()`

11. 將下列 using 陳述式加入至這個檔案：

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. 將下列 `WaitForControlEnabled()` 方法加入至先前識別出有問題的那行程式碼前面：

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. 在 *CodedUITest1.cs* 檔案中，找出 **CodedUITestMethod** 方法，並將對原始 SimpleAppTest ( # A1 方法的參考加上批註或重新命名，然後將它取代為新的 ModifiedSimpleAppTest ( # A3：

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

15. 以滑鼠右鍵按一下 **CodedUITestMethod** 方法，然後選取 [執行測試]。

16. 這次 **自動程式碼** UI 測試成功完成測試中的所有步驟，而且 [ **測試瀏覽器** ] 視窗中會顯示 [成功]。

## <a name="refactor-a-control-in-simplewpfapp"></a>重構 SimpleWPFApp 中的控制項

1. 在 *MainWindow* 的 [設計工具] 中，選取 [button] 控制項。

2. 在 [ **屬性** ] 視窗的頂端，將 [ **名稱** ] 屬性值從 **button1** 變更為 **buttonA**。

3. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

4. 在 [ **測試瀏覽器**] 中，執行 **CodedUITestMethod1**。

     測試失敗，因為自動程式化 UI 測試找不到 UIMap 中原始對應為 button1 的按鈕控制項。 重構是以這種方式影響自動程式化 UI 測試。

5. 在 [測試總管] 視窗的 [StackTrace] 區段中，選擇 **UIMpa.ModifiedSimpleAppTest()** 旁的第一個連結。

     *UIMap.cs* 檔案隨即開啟。 錯誤點反白顯示在程式碼中：

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     請注意，之前在這個程序中的這一行程式碼是使用 `UiStartButton`，這是重構前的 UIMap 名稱。

     若要修正此問題，您可以使用自動程式 **代碼 UI 測試** 產生器，將重構的控制項加入至 UIMap。 您可以將測試的程式碼更新為使用這個程式碼，如下一個程序中所示。

## <a name="map-refactored-control-rerun-the-test"></a>對應重構的控制項以重新執行測試

1. 在 *CodedUITest1.cs* 檔案的 **CodedUITestMethod1 ( # B1** 方法中，以滑鼠右鍵按一下，選取 [ **產生自動程式化 ui 測試的程式碼** ]，然後選擇 [使用自動程式化 **ui 測試** 產生器]。

     **UIMap 自動程式碼 UI 測試** 產生器隨即出現。

2. 使用先前建立的桌面捷徑，執行先前建立的 SimpleWPFApp 應用程式。

3. 在 [UIMap - 自動程式化 UI 測試產生器] 對話方塊上，將交叉線工具拖曳至 SimpleWPFApp 上的 [開始] 按鈕。

     [開始] 按鈕會以藍色方塊括住。 [自動程式化 UI 測試產生器] 需幾秒鐘的時間處理所選控制項的資料並顯示控制項屬性。 請注意，**AutomationUId** 的值為 **buttonA**。

4. 在控制項的屬性中，選擇左上角的箭號展開 [UI 控制項對應]。 請注意，[UIStartButton1] 處於選取狀態。

5. 選擇工具列中的 [將控制項加入至 UI 控制項對應]。

     視窗底部的狀態會顯示 [選取的控制項已經加入到此 UI 控制項對應] 來確認動作。

6. 在 [UIMap - 自動程式化 UI 測試產生器] 對話方塊上，選擇 [產生程式碼]。

     [自動程式化 UI 測試產生器 - 產生程式碼] 對話方塊隨即出現，並帶有注意事項，指出不需要新方法，而且只會針對 UI 控制項對應的變更產生程式碼。

7. 選擇 [產生]。

8. 關閉 SimpleWPFApp。

9. 關閉 **UIMap 自動程式碼 UI 測試** 產生器。

10. 在 **方案總管** 中，開啟 *UIMap.Designer.cs* 檔案。

11. 在 *UIMap.Designer.cs* 檔案中，找出 **UIStartButton1** 屬性。 請注意，`SearchProperties` 已設定為 `"buttonA"`：

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     您現在可以修改自動程式碼 UI 測試來使用新對應的控制項。 如先前的程序所述，如果要在自動程式化 UI 測試中覆寫任何方法或屬性，必須在 *UIMap.cs* 檔案中這麼做。

12. 在 *UIMap.cs* 檔案中，新增函式並指定屬性 `SearchProperties` 的屬性， `UIStartButton` 以使用 `AutomationID` 屬性值為 `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. 在 [ **建置** ] 功能表上，選擇 [ **建置方案**]。

14. 在 [ **測試瀏覽器**] 中，執行 **CodedUITestMethod1**。

     這次自動程式化 UI 測試成功完成測試中的所有步驟。 在 [測試結果] 視窗中，您將會看到 [成功] 的狀態。

## <a name="videos"></a>影片

![影片連結](../data-tools/media/playvideo.gif) [開始使用自動程式化 UI 測試](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>常見問題集

[自動程式化 UI 測試常見問題集](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>另請參閱

- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [自動程式化 UI 測試和動作記錄的支援組態和平台](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [使用自動程式化 UI 測試編輯器來編輯自動程式碼 UI 測試](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
