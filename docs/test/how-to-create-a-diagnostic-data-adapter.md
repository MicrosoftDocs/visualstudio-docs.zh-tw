---
title: 如何：建立診斷資料配接器
description: 瞭解如何使用 Visual Studio 建立類別庫，並新增診斷資料配接器 Api，以建立診斷資料介面卡。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: b35444987686107b9ba2788392abde498661f3de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945145"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>如何：建立診斷資料配接器

若要建立「診斷資料配接器」，您可以使用 Visual Studio 建立類別庫，然後將 Visual Studio Enterprise 提供的診斷資料配接器 API 新增類別庫。 在處理測試回合期間引發的事件時，請以資料流或檔案的形式將您所需要的資訊傳送至架構所提供的 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>。 測試完成時，傳送至 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> 的資料流或檔案會儲存為測試結果的附件。 如果從這些測試結果建立 Bug，或當使用[!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]時，檔案也會連結至 Bug。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以建立診斷資料配接器，其會影響執行測試所在機器，或屬於要用來執行待測應用程式環境的機器。 例如，收集執行測試之測試機器上的檔案，或者收集擔任應用程式之 Web 伺服器角色的機器上的檔案。

您可以為您的診斷資料介面卡提供一個易記的名稱，當您使用 Visual Studio 或 Microsoft Test Manager Visual Studio 2017) 中的 (淘汰時，即會顯示此名稱。 測試設定可讓您定義在執行測試時，要以環境中的哪個電腦角色執行特定診斷資料配接器。 您也可以在建立測試設定時，設定診斷資料配接器。 例如，您可建立從 Web 伺服器收集自訂記錄檔的診斷資料配接器。 當建立測試設定時，您可以選取在執行這個 Web 伺服器角色的一部或多部電腦上執行此診斷資料配接器，並且可以修改測試設定的組態，以只收集最後建立的三個記錄檔。 如需測試設定的詳細資訊，請參閱 [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

當執行測試時會引發事件，如此診斷資料配接器便可以在該時間點執行工作。

> [!IMPORTANT]
> 這些事件可能會在不同的執行緒上引發，尤其是您在多部電腦上執行測試時。 因此，您必須留意可能發生的執行緒問題，並避免不慎損毀自訂配接器的內部資料。 請確定您的診斷資料配接器符合執行緒安全。

以下是您在建立診斷資料配接器時可以使用之關鍵事件的部分清單。 如需診斷資料配接器事件的完整清單，請參閱抽象 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> 類別。

|事件|描述|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|啟動測試回合|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|結束測試回合|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|啟動測試回合中的每個測試|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|結束測試回合中的每個測試|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|啟動測試中的每個測試步驟|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|結束測試中的每個測試步驟|

> [!NOTE]
> 當手動測試完成時，系統不會將其他資料收集事件傳送至診斷資料配接器。 重新執行某項測試時，會使用新的測試案例識別項。 如果使用者在測試期間重設測試 (這會引發 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> 事件)，或變更測試步驟結果，則不會傳送任何資料收集事件至診斷資料配接器，但測試案例識別項仍會相同。 若要判斷測試案例是否已重設，您必須追蹤診斷資料配接器中的測試案例識別項。

使用下列程序建立診斷資料配接器，以收集根據您在建立測試設定時所設定之資訊的資料檔案。

如需診斷資料介面卡專案的完整範例（包括自訂設定編輯器），請參閱 [建立診斷資料介面卡的範例專案](../test/quickstart-create-a-load-test-project.md)。

## <a name="create-and-install-a-diagnostic-data-adapter"></a>建立和安裝診斷資料配接器

1. 建立新的 **類別庫** 專案。

2. 新增組件 **Microsoft.VisualStudio.QualityTools.ExecutionCommon**。

   1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **參考** ]，然後選擇 [ **加入參考** ] 命令。

   2. 選擇 [.NET] 並尋找 **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**。

   3. 選擇 [確定]。

3. 新增組件 **Microsoft.VisualStudio.QualityTools.Common**。

   1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **參考** ]，然後選取 [ **加入參考** ] 命令。

   2. 選擇 [/.NET]，尋找 **Microsoft.VisualStudio.QualityTools.Common.dll**。

   3. 選擇 [確定]。

4. 將下列指示詞新增 `using` 至您的類別檔案：

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. 將 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> 新增至您診斷資料配接器的類別，以將其識別為診斷資料配接器，並且將 **Company**、**Product** 和 **Version** 取代為診斷資料配接器的適當資訊：

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. 將 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> 屬性加入至類別，而將參數取代為診斷資料配接器的適當資訊：

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    這個易記的名稱顯示在測試設定活動中。

   > [!NOTE]
   > 您也可以加入 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>，針對此資料配接器指定自訂組態編輯器的 `Type`，以及選擇性地指定用於編輯器的說明檔。
   >
   > 您也可以套用 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>，將它指定為永遠啟用。

7. 您的診斷資料配接器類別必須繼承自 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> 類別，如下所示：

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. 加入如下的區域變數：

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. 新增 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> 方法和 **Dispose** 方法。 在 `Initialize` 方法中，您可以初始化資料接收器、來自測試設定的任何組態資料，以及註冊您要使用的事件處理常式，如下所示：

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
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
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. 使用下列事件處理常式程式碼和私用方法來收集測試期間產生的記錄檔：

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
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

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
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
    ```

     這些檔案會附加至測試結果。 如果從這些測試結果建立 Bug，或當您使用[!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]時，檔案也會附加至 Bug。

     如果您想要使用自己的編輯器來收集要在測試設定中使用的資料，請參閱 [如何：為您的診斷資料介面卡建立資料的自訂編輯器](../test/quickstart-create-a-load-test-project.md)。

11. 若要在測試完成時根據使用者在測試設定中進行的設定收集記錄檔，您必須建立 *App.config* 檔並且將它加入方案中。 此檔案的格式如下所示，而且必須包含 URI，診斷資料配接器才能識別該檔案。 請將 "Company/ProductName/Version" 替換為實際值。

    > [!NOTE]
    > 如果您不需要為診斷資料配接器設定任何資訊，則不需要建立組態檔。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > 預設組態項目可以包含您需要的任何資料。 如果使用者未在測試設定中設定診斷資料配接器，則在診斷資料配接器執行時預設資料會傳遞給它。 由於您加入至 `<DefaultConfigurations>` 區段的 XML 不可能是宣告之結構描述的一部分，因此您可以忽略它產生的任何 XML 錯誤。
    >
    > 下列路徑中會有其他組態檔範例，取決於您的安裝目錄：*Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*。

     如需詳細資訊，了解如何進行測試設定以在執行測試時使用環境，請參閱[在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)。

     如需安裝設定檔的詳細資訊，請參閱 [如何：安裝自訂診斷資料介面卡](../test/quickstart-create-a-load-test-project.md)

12. 建置方案以建立您的診斷資料配接器組件。

13. 如需安裝自訂編輯器的詳細資訊，請參閱 [如何：安裝自訂診斷資料配接器](../test/quickstart-create-a-load-test-project.md)。

14. 如需詳細資訊，了解如何進行測試設定以在執行測試時使用環境，請參閱[在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)。

15. 若要選取您的診斷資料介面卡，您必須先選取現有的測試設定，或從 Visual Studio 中建立新的測試設定，或在 Visual Studio 2017) 中 Microsoft Test Manager (淘汰。 配接器會顯示在測試設定的 [資料和診斷] 索引標籤上，並使用您指派給類別的易記名稱。

16. 將這些測試設定設定為作用中。 如需測試設定的詳細資訊，請參閱 [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

17. 使用已選取您診斷資料配接器的測試設定來執行您的測試。

    您指定的資料檔案會附加至測試結果。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
- [在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [在測試時收集診斷資料 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [如何：為您的診斷資料介面卡建立資料的自訂編輯器](../test/quickstart-create-a-load-test-project.md)
