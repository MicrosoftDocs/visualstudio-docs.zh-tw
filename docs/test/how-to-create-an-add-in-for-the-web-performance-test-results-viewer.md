---
title: 建立 Web 效能測試結果檢視器的增益集
description: 瞭解如何建立 Visual Studio 增益集，以擴充 Web 效能測試結果檢視器的 UI，並執行擴充 UI 所需的類別。
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: e2773165b37600eb214893de91f8fc8c4467c0d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937624"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>如何：建立 Web 效能測試結果檢視器的增益集

您可以使用下列命名空間來擴充 [Web 效能測試結果檢視器] 的 UI：

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

此外，您還需要加入 LoadTestPackage DLL 的參考，這個 DLL 位於 *% ProgramFiles (x86) % \ Microsoft Visual Studio \\ \<version> \Enterprise\Common7\IDE\PrivateAssemblies* 資料夾。

若要擴充 [Web 效能測試結果檢視器] 的 UI，您必須建立 Visual Studio 增益集和使用者控制項。 下列程序將說明如何建立增益集、使用者控制項，以及如何實作必要的類別，以便擴充 [Web 效能測試結果檢視器] 的 UI。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>建立或開啟包含 ASP.NET Web 應用程式和 Web 效能測試及負載測試專案的方案

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>若要準備擴充 Web 效能測試結果檢視器

建立或開啟您可以用來實驗的非生產環境方案，其中包含 ASP.NET Web 應用程式以及 Web 效能和負載測試專案 (含有 ASP.NET Web 應用程式的一個或多個效能測試)。

> [!NOTE]
> 您可以依照 [如何：建立 web 服務測試](../test/how-to-create-a-web-service-test.md) 並 [產生和執行自動程式化 web 效能測試](../test/generate-and-run-a-coded-web-performance-test.md)中的程式，建立包含 web 效能測試的 ASP.NET web 應用程式和 web 效能和負載測試專案。

## <a name="create-a-visual-studio-add-in"></a>建立 Visual Studio 增益集

增益集是編譯過的 DLL，可以在 Visual Studio 整合式開發環境 (IDE) 中執行。 編譯有助於保護您的智慧財產並且改進效能。 雖然您可以用手動方式建立增益集，但是使用 [增益集精靈] 要簡單許多。 這個精靈會建立基本但實用的增益集，建立完成之後便可立即執行。 當 [增益集精靈] 產生基本程式之後，您就可以加入程式碼並且進行自訂。

[增益集精靈] 可讓您提供增益集的顯示名稱和描述。 這兩項資訊都會顯示在 [增益集管理員] 中。 您可以選擇由精靈產生程式碼，將開啟增益集的命令新增至 [工具] 功能表， 也可以選擇顯示增益集的自訂 [關於] 對話方塊。 當精靈完成時，您就會擁有一個新專案，其中僅包含一個實作增益集的類別。 該類別名為 Connect。

您將在本文的結尾使用 [增益集管理員]。

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>若要使用增益集精靈建立增益集

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案，選擇 [ **加入**]，然後選取 [ **新增專案**]。

2. 建立新的 **Visual Studio 增益集** 專案。

    Visual Studio [增益集精靈] 隨即啟動。

3. 選擇 [下一步]。

4. 在 [選取程式設計語言] 頁面上，選取您要用來撰寫增益集的程式設計語言。

   > [!NOTE]
   > 本主題將針對範例程式碼使用 Visual C#。

5. 在 [選擇主應用程式] 頁面上，選取 [Visual Studio] 並清除 [Visual Studio 巨集]。

6. 選擇 [下一步]。

7. 在 [輸入名稱和描述] 頁面中，鍵入增益集的名稱和描述。

     建立增益集之後，其名稱和描述會顯示在 [增益集管理員] 的 [可用的增益集] 清單中。 您可以為增益集加入詳細的描述資料，讓使用者了解增益集的功能、運作方式等。

8. 選擇 [下一步]。

9. 在 [選擇增益集選項] 頁面上，選取 [當主應用程式啟動時載入增益集]。

10. 清除其餘核取方塊。

11. 在 [[關於] 對話方塊資訊選擇] 頁面上，您可以指定是否要將增益集的相關資訊顯示在 [關於] 對話方塊中。 如果您想要顯示這項資訊，請選取 [是，我希望增益集可以提供 [關於] 對話方塊資訊] 核取方塊。

     可新增至 Visual Studio [關於] 對話方塊的資訊包括版本號碼、支援詳細資料、授權資料等等。

12. 選擇 [下一步]。

13. 您所選取的選項就會顯示在 [摘要] 頁面上，供您檢閱。 如果您對設定感到滿意，請選擇 [完成] 建立增益集。 如果您想要變更某些設定，請選擇 [上一頁] 按鈕。

     此時，系統已建立新的方案和專案，而且新增益集的 *Connect.cs* 檔案會顯示在 [程式碼編輯器] 中。

     完成下列程序之後，您會將程式碼加入至 *Connect.cs* 檔案，以便建立這個 WebPerfTestResultsViewerAddin 專案所參考的使用者控制項。

    建立增益集之後，您必須先將向 Visual Studio 註冊，才能在 [增益集管理員] 中啟動該增益集。 使用具有 *.addin* 副檔名的 XML 檔，即可完成這項作業。

    *.addin* 檔案會描述 Visual Studio 將增益集顯示在 [增益集管理員] 中所需的資訊。 當 Visual Studio 啟動時，它會查看 *.addin* 檔案位置，以尋找可用的 *.addin* 檔案。 如果找到檔案，就會讀取 XML 檔案，並將按一下以啟動增益集時所需的資訊提供給 [增益集管理員]。

    使用 [增益集精靈] 建立增益集時，會自動建立 *.addin* 檔案。

### <a name="add-in-file-locations"></a>增益集檔案位置

[增益集精靈] 會自動建立兩個 *.addin* 檔案的複本，如下所示：

|**.Addin 檔案位置**|**說明**|
|-|----------------------------|-|
|根專案資料夾|用來部署增益集專案。 包含在專案中以便輕鬆編輯，而且具有 XCopy 部署方式的本機路徑。|
|增益集資料夾|用來在偵錯環境中執行增益集。 必須指向目前組建組態的輸出路徑。|

## <a name="create-a-windows-form-control-library-project"></a>建立 Windows Form 控制項程式庫專案

在上一個程序中建立的 Visual Studio 增益集會參考 Windows Form 控制項程式庫專案，以便建立 <xref:System.Windows.Forms.UserControl> 類別的執行個體。

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>若要建立要用於 Web 測試結果檢視器的控制項

1. 在 **方案總管** 中，以滑鼠右鍵按一下方案，選擇 [ **加入**]，然後選取 [ **新增專案**]。

2. 建立新的 **Windows Forms 控制項程式庫** 專案。

3. 從 [工具箱] 中，將 <xref:System.Windows.Forms.DataGridView> 拖曳至 userControl1 的介面上。

4. 按一下 <xref:System.Windows.Forms.DataGridView> 右上角的動作標籤字符 (![智慧標籤字符](../test/media/vs_winformsmttagglyph.gif))，然後依照下列步驟進行操作：

    1. 選擇 [停駐於父容器中]。

    2. 清除下列核取方塊：[啟用新增]、[啟用編輯]、[啟用刪除] 和 [啟用資料行重新調整順序]。

    3. 選擇 [新增資料行]。

         [新增資料行] 對話方塊隨即顯示。

    4. 在 [類型] 下拉式清單中，選取 **DataGridViewTextBoxColumn**。

    5. 清除 [標題文字] 中的文字 "Column1"。

    6. 選擇 [新增]  。

    7. 選擇 [關閉]。

5. 在 [屬性] 視窗中，將 <xref:System.Windows.Forms.DataGridView> 的 [(名稱)] 屬性變更為 **resultControlDataGridView**。

6. 以滑鼠右鍵按一下設計介面，然後選取 [檢視程式碼]。

     *UserControl1.cs* 檔案就會顯示在 [程式碼編輯器] 中。

7. 將具現化 <xref:System.Windows.Forms.UserControl> 類別的名稱從 UserContro1 變更為 resultControl：

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     在下一個程序中，您會將程式碼加入至 WebPerfTestResultsViewerAddin 專案的 *Connect.cs* 檔案，而這個檔案將會參考 resultControl 類別。

     您稍後會將其他程式碼加入至 *Connect.cs* 檔案。

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>將程式碼加入至 WebPerfTestResultsViewerAddin

1. 在 [方案總管] 中，以滑鼠右鍵按一下 WebPerfTestResultsViewerAddin 專案中的 [參考] 節點，然後選取 [新增參考]。

2. 在 [新增參考] 對話方塊中，選擇 [.NET] 索引標籤。

3. 向下捲動並選取 **Microsoft.VisualStudio.QualityTools.WebTestFramework** 和 **System.Windows.Forms**。

4. 選擇 [確定]。

5. 再次以滑鼠右鍵按一下 [參考] 節點，然後選取 [新增參考]。

6. 在 [新增參考] 對話方塊中，選擇 [瀏覽] 索引標籤。

7. 選擇 [查詢] 下拉式清單並巡覽至 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*，然後選取 *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* 檔案。

8. 選擇 [確定]。

9. 以滑鼠右鍵按一下 WebPerfTestResultsViewerAddin 專案節點，然後選取 [新增參考]。

10. 在 [新增參考] 對話方塊中，選擇 [專案] 索引標籤。

11. 在 [專案名稱] 底下，選取 **WebPerfTestResultsViewerControl** 專案，然後選擇 [確定]。

12. 如果 *Connect.cs* 檔案仍未開啟，請在 [方案總管] 中，以滑鼠右鍵按一下 WebPerfTestResultsViewerAddin 專案中的 **Connect.cs** 檔案，然後選取 [檢視程式碼]。

13. 在 *Connect.cs* 檔案中，加入下列 Using 陳述式：

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. 向下捲動至 *Connect.cs* 檔案的底部。 您必須針對 <xref:System.Windows.Forms.UserControl> 加入 GUID 清單，以防開啟多個 [Web 效能測試結果檢視器] 執行個體。 您稍後將會加入使用這份清單的程式碼。

     第二份字串清單會用於您稍後編寫程式碼的 OnDiscconection 方法。

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* 檔案會根據 <xref:Extensibility.IDTExtensibility2> 類別具現化名為 Connect 的類別，而且也包括一些用於實作 Visual Studio 增益集的方法。 其中一個方法是 OnConnection 方法，這個方法會接收載入增益集的通知。 在 OnConnection 方法中，您將會使用 LoadTestPackageExt 類別來建立 [Web 效能測試結果檢視器] 的擴充性套件。 將下列程式碼新增至 OnConnection 方法：

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. 將下列程式碼加入至 Connect 類別，以便針對您在 OnConnection 方法中加入的 loadTestPackageExt.WebTestResultViewerExt.WindowCreated 事件處理常式建立 WebTestResultViewerExt_WindowCreated 方法以及 WebTestResultViewerExt_WindowCreated 方法所呼叫的 WindowCreated 方法。

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. 將下列程式碼加入至 Connect 類別，以便針對您在 OnConnection 方法中加入的 loadTestPackageExt.WebTestResultViewerExt.SelectionChanged 事件處理常式建立 WebTestResultViewer_SelectedChanged 方法：

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. 將下列程式碼加入至 Connect 類別，以便針對您在 OnConnection 方法中加入的 loadTestPackageExt.WebTestResultViewerExt.WindowClosed 事件處理常式建立 WebTesResultViewer_WindowClosed 方法：

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     現在 Visual Studio 增益集的程式碼已經完成，您必須將 Update 方法加入至 WebPerfTestResultsViewerControl 專案中的 resultControl。

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>將程式碼加入至 WebPerfTestResultsViewerControl

1. 在 [方案總管] 中，以滑鼠右鍵按一下 WebPerfTestResultsViewerControl 專案節點，然後選取 [屬性]。

2. 選取 [應用程式] 索引標籤，然後選擇 [目標 Framework] 下拉式清單並選取 [.NET Framework 4] (或更新版本)。 關閉 [ **屬性** ] 視窗。

   這是支援擴充 [Web 效能測試結果檢視器] 所需之 DLL 參考的必要步驟。

3. 在 [方案總管] 的 WebPerfTestResultsViewerControl 專案中，以滑鼠右鍵按一下 [參考] 節點，然後選取 [新增參考]。

4. 在 [新增參考] 對話方塊中，按一下 [.NET] 索引標籤。

5. 向下捲動並選取 **Microsoft.VisualStudio.QualityTools.WebTestFramework**。

6. 選擇 [確定]。

7. 在 *UserControl1.cs* 檔案中，加入下列 Using 陳述式：

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. 加入從 *Connect.cs* 檔案中 WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged 方法呼叫並傳遞 WebTestRequestResult 的 Update 方法。 Update 方法會將 WebTestRequestResult 傳遞給它的各種屬性填入 DataGridView。

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>建立解決方案

- 在 [建置] 功能表上，選取 [建置方案]。

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>登錄 WebPerfTestResultsViewerAddin 增益集

1. 在 [工具] 功能表上，選取 [增益集管理員]。

2. [增益集管理員] 對話方塊隨即顯示。

3. 在 [可用的增益集] 資料行中，選取 WebPerfTestResultsViewerAddin 增益集的核取方塊，並且清除 [啟動] 和 [命令列] 資料行下方的核取方塊。

4. 選擇 [確定]。

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>使用 Web 測試結果檢視器執行 Web 效能測試

1. 執行 Web 效能測試，然後您將會看見 WebPerfTestResultsViewerAddin 增益集中名為 Sample 的新索引標籤顯示在 [Web 效能測試結果檢視器] 中。

2. 選擇此索引標籤可查看 DataGridView 中呈現的屬性。

## <a name="net-security"></a>.NET 安全性

為了改善安全性，防止惡意的增益集自動啟動，Visual Studio 在名為 [增益集/巨集安全性] 的 [工具選項] 頁面中提供相關設定。

此外，這個選項頁還可讓您指定 Visual Studio 搜尋 *.AddIn* 登錄檔案的資料夾。 這樣做可讓您限制系統能讀取 *.AddIn* 登錄檔案的位置，藉以改善安全性。 這有助於避免您不小心使用惡意 *.AddIn* 檔案。

**增益集安全性設定**

增益集安全性之選項頁中的設定如下：

- **允許載入增益集元件**： 依預設為已選取。 當您選取此選項時，就可以在 Visual Studio 中載入增益集。 當您沒有選取此選項時，則禁止在 Visual Studio 中載入增益集。

- **允許從 URL 載入增益集元件**： 預設不會選取。 當您選取此選項時，就可以從外部網站載入增益集。 當您沒有選取此選項時，則禁止在 Visual Studio 中載入遠端增益集。 如果增益集因為某種原因無法載入，那麼便無法從網路載入。 這項設定只能控制增益集 DLL 的載入。 *.Addin* 登錄檔案必須隨時位於本機系統中。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [為負載測試建立自訂程式碼和外掛程式](../test/create-custom-code-and-plug-ins-for-load-tests.md)
