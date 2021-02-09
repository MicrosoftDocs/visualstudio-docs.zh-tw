---
title: 使用自動程式化 UI 測試來測試 UWP 應用程式
description: 瞭解如何建立通用 Windows 平臺應用程式的自動程式碼 UI 測試，方法是建立 UWP 應用程式來測試及建立自動程式化 UI 測試。
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 0fb60de87fa98e4715d872512c120a408ec8339e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911520"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>建立自動程式化 UI 測試來測試 UWP 應用程式

本文說明如何建立通用 Windows 平台 (UWP) 應用程式的自動程式化 UI 測試。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>建立要測試的 UWP 應用程式

第一個步驟是建立簡單的 UWP 應用程式來執行測試。

1. 在 Visual Studio 中，使用適用於 Visual C# 或 Visual Basic 的 [空白應用程式 (通用 Windows)] 範本建立新的專案。

   ::: moniker range="vs-2017"

   ![空白應用程式 (通用 Windows) 範本](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. 在 [新增通用 Windows 平台專案] 對話方塊中，選取 [確定] 以接受預設平台版本。

1. 從 [方案總管] 中，開啟 *MainPage.xaml*。

   該檔案隨即在 [XAML 設計工具] 中開啟。

1. 將按鈕控制項和文字方塊控制項從 [工具箱] 中拖曳至設計介面。

     ![設計 UWP 應用程式](../test/media/toolbox-controls.png)

1. 提供控制項的名稱。 選取文字方塊控制項，然後在 [屬性] 視窗的 [名稱] 欄位中輸入 **textBox**。 選取按鈕控制項，然後在 [屬性] 視窗的 [名稱] 欄位中輸入 **button**。

1. 按兩下按鈕控制項，並將下列程式碼新增至 `Button_Click` 方法的主體。 此程式碼只會將文字方塊中的文字設定為按鈕控制項的名稱，這只是為了提供一些資料，藉以驗證我們稍後將建立的自動程式化 UI 測試。

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. 按下 **Ctrl** + **F5** 以執行應用程式。 您應該會看到如下的內容：

   ![含有按鈕和文字方塊的 UWP 應用程式](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>建立自動程式碼 UI 測試

1. 若要將測試專案新增至方案，請在 [方案總管] 中，以滑鼠右鍵按一下方案，並選擇 [新增] > [新增專案]。

1. 搜尋並選取 [自動程式化 UI 測試專案 (通用 Windows)] 範本。

   ::: moniker range="vs-2017"

   ![新增自動程式化 UI 測試專案](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > 如果您沒有看到 [自動程式化 UI 測試專案 (通用 Windows)] 範本，則需要[安裝自動程式化 UI 測試元件](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)。

1. 在 [產生自動程式化 UI 測試的程式碼] 對話方塊中，選取 [手動編輯測試]。

   ![[產生自動程式化 UI 測試的程式碼] 對話方塊](../test/media/manually-edit-the-test.png)

1. 如果您的 UWP 應用程式尚未執行，請按 **Ctrl** + **F5** 啟動它。

1. 開啟 [自動程式化 UI 測試產生器] 對話方塊，方法是將游標置於 `CodedUITestMethod1` 方法，然後選擇 [測試] > [產生自動程式化 UI 測試的程式碼] > [使用自動程式化 UI 測試產生器]。

1. 將控制項新增至 UI 控制項對應。 使用 [自動程式化 UI 測試產生器] 交叉線工具，選取 UWP 應用程式中的按鈕控制項。 在 [新增判斷提示] 對話方塊中，如果有必要，請展開 [UI 控制項對應] 窗格，然後選取 [將控制項新增至 UI 對應]。

     ![將控制項加入至 UI 對應](../test/media/add-control-to-ui-control-map.png)

1. 請重複上一個步驟，將文字方塊控制項新增至 UI 控制項對應。

1. 在 [自動程式化 UI 測試產生器] 對話方塊中，選取 [產生程式碼] 或按 **Ctrl**+**G**。 然後選取 [產生]，為 UI 控制項對應的變更建立程式碼。

     ![產生 UI 對應的程式碼](../test/media/generate-code-dialog.png)

1. 若要確認按一下按鈕時，文字方塊中的文字會變更為 **button**，請按一下該按鈕。

     ![按一下按鈕控制項以設定 Textbox 值](../test/media/uwp-app-button-textbox.png)

1. 新增判斷提示，以確認文字方塊控制項中的文字。 使用交叉線工具選取文字方塊控制項，然後在 [新增判斷提示] 對話方塊中選取 [文字] 屬性。 然後，選取 [新增判斷提示] 或按 **Alt**+**A**。 在 [判斷提示失敗的訊息] 方塊中，輸入 **extbox value is unexpected.**， 然後選取 **[確定]**。

     ![使用交叉線工具選擇文字方塊新增判斷提示](../test/media/add-assertion-for-text.png)

1. 產生判斷提示的測試程式碼。 在 [自動程式化 UI 測試產生器] 對話方塊中，選取 [產生程式碼]。 在 [產生程式碼] 對話方塊中，選取 [新增並產生]。

     ![產生 Textbox 判斷提示的程式碼](../test/media/add-and-generate-assert-method.png)

   在 [方案總管] 中，開啟 *UIMap.Designer.cs*，以檢視針對 assert 方法和控制項所新增的程式碼。

   > [!TIP]
   > 如果您要使用 Visual Basic，請開啟 *CodedUITest1.vb*。 然後，在 `CodedUITestMethod1()` 測試方法程式碼中，以滑鼠右鍵按一下對 assert 方法 `Me.UIMap.AssertMethod1()` 的呼叫，並選擇 [移至定義]。 *UIMap.Designer.vb* 隨即會在程式碼編輯器中開啟，您可以檢視針對 assert 方法和控制項所新增的程式碼。

    > [!WARNING]
    > 請勿直接修改 *UIMap.designer.cs* 或 *UIMap.Designer.vb* 檔案。 如果這樣做，則在產生測試時，將會覆寫您的變更。

    Assert 方法看起來像這樣：

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. 接下來，我們需要取得想要測試之 UWP [應用程式](#create-a-uwp-app-to-test)的 **AutomationId**。 開啟 Windows [開始] 功能表來查看應用程式磚。 然後，將交叉線工具 ![目標圖示](media/target-icon.png) 從 [自動程式化 UI 測試產生器] 對話方塊，拖曳至應用程式磚。 當藍色方塊圍繞著磚時，請放開滑鼠。

   ![交叉線工具](media/cross-hair-tool.png)

   [新增判斷提示] 對話方塊隨即開啟，並顯示應用程式的 **AutomationId**。 以滑鼠右鍵按一下 **AutomationId**，並選擇 [將值複製到剪貼簿]。

   ![[新增判斷提示] 對話方中的 AutomationID](../test/media/automation-id.png)

1. 將程式碼新增至測試方法，以啟動 UWP 應用程式。 在 [方案總管] 中，開啟 *CodedUITest1.cs* 或 *CodedUITest1.vb*。 在上述對 `AssertMethod1` 的呼叫中，新增程式碼以啟動 UWP 應用程式：

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   將範例程式碼的自動化識別碼，取代為您在上一個步驟中複製到剪貼簿的值。

   > [!IMPORTANT]
   > 請修剪自動化識別碼的開頭以移除字元，例如 **P~**。 如果您不會修剪這些字元，則當它嘗試啟動應用程式時，測試會擲回 `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException`。

1. 接下來，將程式碼新增至測試方法以按一下按鈕。 在 `XamlWindow.Launch` 的下一行，新增手勢來點選按鈕控制項：

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   新增程式碼之後，完整的 `CodedUITestMethod1` 測試方法應該顯示如下：

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. 建置測試專案，然後選取 [測試] > [視窗] > [測試總管] 來開啟 [測試總管]。

1. 選擇 [全部執行] 以執行測試。

   應用程式隨即開啟，點選按鈕，並在文字方塊的 [文字] 屬性中填入。 Assert 方法會驗證文字方塊的 [文字] 屬性。

   測試完成之後，[測試總管] 會顯示測試成功。

   ![通過的測試在 [測試總管] 中顯示](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>問答集

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>問：為什麼在 [產生自動程式化 UI 測試的程式碼] 對話方塊中看不到錄製自動程式化 UI 測試的選項？

**答**：UWP 應用程式不支援錄製選項。

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>問：我可以根據 WinJS 建立 UWP 應用程式的自動程式化 UI 測試嗎？

**答**：不可以，目前只支援以 XAML 為基礎的應用程式。

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>問：為什麼無法修改 UIMap.Designer 檔案中的程式碼？

**答**：每次您使用 [自動程式化 UI 測試產生器] 產生程式碼時，對 *UIMapDesigner.cs* 檔案中的程式碼所做的變更都會被覆寫。 如果您需要修改錄製的方法，請將它複製到 *UIMap.cs* 檔案並重新命名。 *UIMap.cs* 檔案可用來覆寫 *UIMapDesigner.cs* 檔案中的方法和屬性。 請移除 *CodedUITest.cs* 檔案中原始方法的參考，並將它取代為重新命名的方法名稱。

## <a name="see-also"></a>另請參閱

- [使用 UI 自動化來測試您的程式碼](../test/use-ui-automation-to-test-your-code.md)
- [為 UWP 控制項設定獨特的自動化屬性](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
