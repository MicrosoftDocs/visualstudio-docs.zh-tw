---
title: Visual Studio 中用於建立診斷資料配接器的範例專案
ms.date: 10/19/2016
ms.topic: sample
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b7d2cd30faa5cbc5b4f8626c17de77c68bdf8bae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977111"
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>建立診斷資料配接器的範例專案

"MyDiagnosticDataAdapter" 是一個簡易的診斷資料配接器，可在您執行測試時將記錄檔附加至測試結果。

 在安裝診斷資料收集器或組態編輯器的電腦上，您必須具有其系統管理權限。

## <a name="example-data-adapter"></a>範例資料配接器

本範例示範如何執行下列工作：

-   套用屬性讓 Microsoft Test Manager 可發現某個類別，而將其作為診斷資料配接器。

-   套用屬性讓 Microsoft Test Manager可發現某個使用者控制項類別，而將其作為可用來變更診斷資料配接器組態的編輯器。

-   存取預設組態資料。

-   註冊特定的診斷資料收集事件。

-   藉由將記錄檔傳送至 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> 來附加記錄檔。

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>範例組態編輯器

這是診斷資料配接器的範例組態編輯器。 請將使用者控制項加入至專案中，並以標籤 ("Name of Log File:") 和名為 "FileTextBox" 的文字方塊，建立簡單的表單。

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

            string result = String.Empty;
            if (files.Count > 0)
            {
                XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result = pathAttribute.Value;
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-file"></a>範例組態檔

以下是診斷資料收集器組態編輯器的範例組態檔。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>編譯程式碼

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>建立此診斷配接器的程式碼專案

1.  建立名為 "MyDataCollector" 的新類別庫專案。

2.  在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [屬性]。 若要選取要新增的資料夾，請選擇 [參考路徑]，然後選擇省略符號 (**…**)。

     [選取參考路徑] 對話方塊隨即顯示。

3.  根據您的安裝目錄選取下列路徑：*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*。 選擇 [確定] 。

4.  若要將資料夾新增至參考路徑，請選擇 [新增資料夾]。

     資料夾會顯示在參考路徑清單中。

5.  選擇**全部儲存**圖示，儲存參考路徑。

6.  新增組件 **Microsoft.VisualStudio.QualityTools.ExecutionCommon**。

    1.  在 [方案總管] 中，以滑鼠右鍵按一下 [參考]，然後選擇 [新增參考]。

    2.  選擇 [瀏覽] 並尋找 **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**。

         此組件將位於 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* 中。

    3.  選擇 [確定] 。

7.  新增組件 **Microsoft.VisualStudio.QualityTools.Common**。

    1.  在 [方案總管] 中，以滑鼠右鍵按一下 [參考]，然後選取 [新增參考]。

    2.  選擇 [瀏覽] 並尋找 **Microsoft.VisualStudio.QualityTools.Common.dll**。

         此組件將位於 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* 中。

    3.  選擇 [確定] 。

8.  將本文件前段所列的診斷資料配接器類別，複製到您類別庫的類別中。 儲存此類別。

9. 若要將使用者控制項新增至專案，以滑鼠右鍵按一下 [方案總管] 中的 [MyDataCollector] 專案，指向 [新增]，然後選擇 [使用者控制項]。 選擇 [新增]。

10. 使用工具列，將標籤新增至使用者控制項，然後將 [Text] 屬性變更為 [檔案名稱:]。

11. 使用工具列，將文字方塊新增至使用者控制項，然後將名稱變更為 **textBoxFileName**。

12. 以滑鼠右鍵按一下 [方案總管] 中的使用者控制項，然後選擇 [檢視程式碼]。 將此使用者控制項類別取代為本文件前段所列的使用者控制項類別。 儲存此類別。

    > [!NOTE]
    > 根據預設，使用者控制項的名稱是 UserControl1。 請確定使用者控制項類別程式碼使用的是您的使用者控制項名稱。

13. 若要建立組態檔，以滑鼠右鍵按一下 [方案總管] 中的方案，指向 [新增]，然後選擇 [新增項目]。 選擇以選取 [應用程式組態檔]，然後選擇 [新增]。 隨即將名為 **App.config** 的檔案新增至您的方案中。

14. 將先前提供之範例中的 XML 複製到 XML 檔中。 儲存檔案。

15. 建置方案，然後將建置的組件和 `App.config` 檔案複製到 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors* 目錄中。

16. 建立使用此自訂資料診斷配接器的測試設定。 設定用以收集現存檔案的測試設定。

     如果您從 Microsoft Test Manager 執行測試，您可以在執行測試前將這些測試設定指派給測試計劃，或使用 [以選項執行] 命令來指派測試設定和覆寫測試設定。 如需測試設定的詳細資訊，請參閱[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

17. 使用已選取您診斷資料配接器的測試設定來執行您的測試。

     執行測試時，您所指定的資料檔案會附加至測試結果中。

## <a name="see-also"></a>另請參閱

- [如何：建立診斷資料配接器](../test/how-to-create-a-diagnostic-data-adapter.md)
- [如何：為您的診斷資料配接器建立資料的自訂編輯器](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [如何：安裝自訂的診斷資料配接器](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [建立診斷資料配接器以收集自訂資料或影響測試電腦](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)