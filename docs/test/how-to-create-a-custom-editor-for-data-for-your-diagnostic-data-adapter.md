---
title: 在 Visual Studio 中為診斷資料配接器建立自訂資料編輯器
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 41008d1c2808a5a6e6428670a3e7dbbf1041caee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819335"
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>如何：為您的診斷資料配接器建立資料的自訂編輯器

當您建立診斷資料配接器時，可以讓終端使用者在選取您的自訂診斷資料配接器以用於其測試設定時，能夠設定特定資料。 例如，您可以選取組態資料，以指定要擷取哪些登錄機碼、要模擬何種網路負載層級，或是要在哪個目錄中尋找要附加的暫存檔或工作檔案。

您必須使用組態檔，為您的診斷資料配接器設定初始值。 您可以提供自訂編輯器，讓使用者可以修改組態資料。

若要建立您自己的編輯器，您必須建立實作了 <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> 的使用者控制項。

診斷資料配接器可以使用 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>，來指定用於編輯診斷資料組態設定的編輯器類別。

您也會指定要使用的預設組態資料。  如需範例預設組態，請參閱[建立診斷資料配接器的範例專案](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)。

使用下列程序建立自訂編輯器，以在有使用者使用您的自訂資料診斷配接器時，更新測試設定的資料。

> [!NOTE]
> 若要建立自訂編輯器，您必須先建立已將 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> 套用至此類別的診斷資料配接器。 您可以在該屬性 (Attribute) 中使用選擇性 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*> 屬性 (Property) 來指定編輯器的說明內容來源。 如需如何建立診斷資料配接器的詳細資訊，請參閱[如何：建立診斷資料配接器](../test/how-to-create-a-diagnostic-data-adapter.md)。

如需診斷資料配接器專案的完整範例 (包括自訂組態編輯器)，請參閱[建立診斷資料配接器的專案範例](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)。

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>為您的診斷資料配接器建立自訂編輯器

1. 在專案中為您的資料診斷配接器建立使用者控制項：

   1.  以滑鼠右鍵按一下包含診斷資料配接器類別的專案，指向 [新增]，然後指向 [使用者控制項]。

   2.  在此範例中，請將文字為 **Data File Name:** 的標籤和名為 **FileTextBox** 的文字方塊新增至表單，讓使用者輸入必要的資料。

   > [!NOTE]
   > 目前僅支援 Windows Forms 使用者控制項。

2. 將下列程式碼行加入至宣告區段：

   ```csharp
   using System.Xml;
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   ```

3. 將此使用者控制項放入自訂編輯器中。

   1.  以滑鼠右鍵按一下程式碼專案中的使用者控制項，然後指向 [檢視程式碼]。

   2.  設定類別以實作編輯器介面 <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>，如下所示：

   ```csharp
   public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
   ```

   1.  以滑鼠右鍵按一下程式碼中的 <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>，然後選取 [實作介面] 命令。 您必須為此介面實作的方法會加入至您的類別中。

   2.  將 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> 新增至您的使用者控制項，讓您的編輯器將其識別為診斷資料配接器編輯器，並將 [公司]、[產品] 和 [版本] 取代為診斷資料配接器的適當資訊：

       ```csharp
       [DataCollectorConfigurationEditorTypeUri(
           "configurationeditor://MyCompany/MyConfigEditor/1.0")]
       ```

4. 加入兩個私用變數，如下所示：

   ```csharp
   private DataCollectorSettings collectorSettings;
   private IServiceProvider ServiceProvider { get; set; }
   ```

5. 加入程式碼以初始化診斷資料配接器的編輯器。 您可以使用 settings 變數中的資料，將預設值加入至使用者控制項中的欄位。 此資料是指位於 XML 組態檔中，您配接器之 `<DefaultConfiguration>` 項目中的資料。

   ```csharp
   public void Initialize(
       IServiceProvider svcProvider,
       DataCollectorSettings settings)
   {
       ServiceProvider = svcProvider;
       collectorSettings = settings;

       // Display the default file name as listed in the settings file.
       this.SuspendLayout();
       this.FileTextBox.Text = getText(collectorSettings.Configuration);
       this.ResumeLayout();
   }
   ```

6. 加入程式碼，以將您編輯器中的控制項資料儲存回診斷資料配接器 API 所需的 XML 格式，如下所示：

   ```csharp
   public DataCollectorSettings SaveData()
   {
       collectorSettings.Configuration.InnerXml =
           String.Format(
   @"<MyCollectorName
       xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
     <File FullPath=""{0}"" />
   </MyCollectorName>",
       FileTextBox.Text);
       return collectorSettings;
   }
   ```

7. 如果對您來說很重要，請加入程式碼以驗證 `VerifyData` 方法中的資料正確無誤，或者讓方法傳回 `true`。

   ```csharp
   public bool VerifyData()
   {
       // Not currently verifying data
       return true;
   }
   ```

8. (選擇性) 您可以加入程式碼，以將資料重設為 `ResetToAgentDefaults()` 方法 (使用私用 `getText()` 方法) 中的 XML 組態檔所提供的初始設定。

   ```csharp
   // Reset to default value from XML configuration
   // using a custom getText() method
   public void ResetToAgentDefaults()
   {
       this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
   }

   // Local method to read the configuration settings
   private string getText(XmlElement element)
   {
       // Setup namespace manager with our namespace
       XmlNamespaceManager nsmgr =
           new XmlNamespaceManager(
               element.OwnerDocument.NameTable);

       // Find all the "File" elements under our configuration
       XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

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
   ```

9. 建置您的方案。 根據您的安裝目錄，將診斷資料配接器組件和 XML 組態檔 (`<diagnostic data adapter name>.dll.config`) 複製到下列位置：*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*。

    > [!NOTE]
    > 雖然組態編輯器和診斷資料配接器的所在專案和組件可以不同，但也可以位於相同的組件中。

10. 若要在測試中使用診斷資料配接器，您必須從現有的測試設定清單中選取，或是從 Microsoft Test Manager 或 Visual Studio 建立新的設定，然後選取診斷資料配接器。

     配接器會顯示在測試設定的 [資料和診斷] 索引標籤上，並使用您指派給類別的易記名稱。

11. 若要設定測試設定所需的診斷資料配接器，請選擇配接器名稱旁邊的 [設定]。

     您的自訂編輯器隨即顯示。

12. 視需要在自訂編輯器中編輯欄位，然後選擇 [儲存]。

13. 如果您從 Microsoft Test Manager 執行測試，您可以在執行測試前將這些測試設定指派給測試計劃，或使用 [以選項執行] 命令來指派測試設定和覆寫測試設定。 如需測試設定的詳細資訊，請參閱[使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)。

14. 在可以使用新的組態編輯器搭配診斷資料配接器之前，您必須將 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> 套用至要使用編輯器的每個診斷資料配接器類別，然後在用戶端電腦上重新編譯和重新安裝這些類別。 如需如何安裝診斷資料配接器和組態編輯器的詳細資訊，請參閱[如何：安裝自訂的診斷資料配接器](../test/how-to-install-a-custom-diagnostic-data-adapter.md)。

15. 使用已選取您診斷資料配接器的測試設定來執行您的測試。

     您在編輯器中指定的資料檔案會附加至測試結果中。

    如需如何設定測試設定以便在執行測試時使用環境的詳細資訊，請參閱[測試時收集診斷資料 (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) 或[在手動測試中收集診斷資料 (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [建立診斷資料配接器以收集自訂資料或影響測試電腦](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
- [建立診斷資料配接器的範例專案](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)