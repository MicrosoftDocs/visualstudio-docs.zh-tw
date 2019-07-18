---
title: 部署 Visual Studio 中 SharePoint 工具擴充功能 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53e36d993e72da759c87e7d2d2f908818b3d9024
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580640"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>部署適用於 Visual Studio 中 SharePoint 工具擴充功能

若要部署的 SharePoint 工具延伸模組，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝，其中包含延伸模組組件和任何其他您想要將副檔名的檔案。 VSIX 封裝是壓縮的檔案，遵循開放封裝慣例 (OPC) 標準。 VSIX 封裝，需要 *.vsix*延伸模組。

建立 VSIX 封裝之後，其他使用者可以執行安裝擴充功能的.vsix 檔案。 當使用者安裝您的延伸模組時，所有的檔案會安裝到 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions 資料夾。 若要部署的延伸模組，您可以上傳至 VSIX 封裝[Visual Studio Marketplace](https://marketplace.visualstudio.com/)網站上，或者您可以將套件發佈至您的客戶透過其他方法，例如裝載在網路共用或某些其他網頁套件站台。

如需有關建立 VSIX 封裝和部署他們[Visual Studio Marketplace](https://marketplace.visualstudio.com/)，請參閱[運送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。

 您可以使用，以建立 VSIX 封裝**VSIX 專案**範本在 Visual Studio 中，或者您可以手動建立 VSIX 封裝。

## <a name="use-vsix-projects-to-create-vsix-packages"></a>使用 VSIX 專案建立 VSIX 封裝

您可以使用**VSIX 專案**Visual Studio SDK 來建立 VSIX 封裝 SharePoint 工具擴充功能所提供的範本。 使用 VSIX 專案透過手動建立 VSIX 封裝提供數個優點：

- 當您建置專案時，visual Studio 會自動產生 VSIX 封裝。 為您完成工作，例如將部署檔案新增至套件，以及建立封裝的 [Content_Types].xml 檔案。

- 您可以設定 VSIX 套件中包含擴充功能專案和其他檔案，例如專案範本和項目範本的建置輸出的 VSIX 專案。

如需使用 VSIX 專案的詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。

### <a name="organize-your-projects"></a>組織您的專案

根據預設，VSIX 專案只會產生 VSIX 封裝，而不是組件。 因此，您通常不會實作 SharePoint 工具擴充功能的 VSIX 專案中。 您通常會使用至少兩個專案：

- VSIX 專案。

- 實作您的擴充功能的類別庫專案。

您可能也使用其他專案針對特定類型的延伸模組：

- 實作您的延伸模組所使用的任何 SharePoint 命令的類別庫專案。 如需示範此案例的逐步解說，請參閱[逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。

- 如果您的延伸模組會定義新類型的 SharePoint 專案項目建立項目範本或專案範本的項目範本或專案範本專案。 如需示範此案例的逐步解說，請參閱[逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。

- 如果您的延伸模組包含的範本實作的項目範本或專案範本的自訂精靈類別庫專案。 如需示範此案例的逐步解說，請參閱[逐步解說：建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。

如果您在相同的 Visual Studio 方案中包含的所有專案，您可以修改 source.extension.vsixmanifest 檔案中，在 VSIX 專案，以包含的類別庫專案的組建輸出。

### <a name="edit-the-vsix-manifest"></a>編輯 VSIX 資訊清單

您必須編輯 source.extension.vsixmanifest 檔案中的 VSIX 專案，以包含您想要在您的延伸模組中包含的所有項目的項目。 當您從其捷徑功能表開啟 source.extension.vsixmanifest 檔案中時，檔案會出現在設計工具中，提供了 UI 供編輯的 XML 檔案中。 如需詳細資訊，請參閱 < [VSIX 資訊清單設計工具](../extensibility/vsix-manifest-designer.md)。

您必須在 source.extension.vsixmanifest 檔案中的下列項目中新增項目：

- 延伸模組組件中。

- 實作您的延伸模組所使用的任何 SharePoint 命令的組件。

- 任何專案範本或與您的延伸模組相關聯的項目範本。

- 範本與您的延伸模組相關聯的自訂精靈。

下列程序描述如何將項目新增至的.vsixmanifest 檔案中，針對每個這些項目。

#### <a name="to-include-the-extension-assembly"></a>包含延伸模組組件

1. 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後再選擇**開啟**。

     設計工具中開啟檔案

2. 上**資產**索引標籤的 編輯器 中，選擇**新增** 按鈕。

     **加入新資產**對話方塊隨即開啟。

3. 在 **型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。

4. 在 **來源**清單中，執行下列步驟：

    - 如果延伸模組組件是從專案和 VSIX 專案相同的方案中，選擇**目前的方案中的專案**。 在 **專案**清單中，選擇專案的名稱。

    - 如果延伸模組組件包含為您的專案中的檔案，請選擇**檔案系統上的**。 在 **路徑**清單中，延伸模組組件檔案中，輸入完整路徑或使用**瀏覽**按鈕，以找出並選擇 組件檔案。

5. 選擇 [確定]  按鈕。

#### <a name="to-include-a-sharepoint-command-assembly"></a>要包含的 SharePoint 命令的組件

1. 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後再選擇**開啟** 按鈕。

     在設計工具中，開啟檔案。

2. 在 **資產**區段的編輯器中，選擇**新增**按鈕。

     **加入新資產**對話方塊隨即開啟。

3. 在 **型別**方塊中，輸入**SharePoint.Commands.v4**。

4. 在 **來源**清單中，執行下列步驟：

    - 如果從同一個 VSIX 專案與方案中的專案在建置命令組件，請選擇**目前的方案中的專案**。 在 **專案**清單中，選擇專案的名稱。

    - 如果命令組件包含為您的專案中的檔案，請選擇**檔案系統上的**。 在 **路徑**清單中，延伸模組組件檔案中，輸入完整路徑或使用**瀏覽**按鈕，以找出並選擇 組件檔案。

5. 選擇 [確定]  按鈕。

#### <a name="to-include-a-template-that-you-create"></a>若要包含您所建立的範本

1. 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後再選擇**開啟** 按鈕。

     在設計工具中，開啟檔案。

2. 在 **資產**區段的編輯器中，選擇**新增**按鈕。

     **加入新資產**對話方塊隨即開啟。

3. 在 **型別**清單中，選擇**Microsoft.VisualStudio.ProjectTemplate**或是**Microsoft.VisualStudio.ItemTemplate**。

4. 在 **來源**清單中，選擇**目前方案中的專案**。

5. 在 [**專案**清單中，選擇專案的名稱，然後選擇**確定**] 按鈕。

6. 在 **方案總管**，開啟專案範本或項目範本專案的捷徑功能表，然後選擇**卸載專案**。

7. 同樣地，開啟專案節點的捷徑功能表，然後選擇**編輯**_YourTemplateProjectName_**.csproj**或是**編輯**_YourTemplateProjectName_**.vbproj**。

8. 找出下列`VSTemplate`專案檔中的項目。

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. 這個項目取代為下列 XML 程式碼。

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`項目會指定當您建置專案時，專案範本建立所在的路徑中的其他資料夾。 此處指定的資料夾，確保項目範本會提供，客戶開啟時，才**加入新的專案**對話方塊方塊中，展開**SharePoint**節點，然後選擇  **2010年**節點。

10. 儲存並關閉檔案。

11. 在 **方案總管**，開啟專案範本或項目範本的專案的捷徑功能表，然後選擇**重新載入專案**。

#### <a name="to-include-a-template-that-you-create-manually"></a>若要包含您以手動方式建立的範本

1. 在 VSIX 專案中，新增至專案，以包含範本的資料夾。

2. 在這個新的資料夾中，建立下列子資料夾中，，然後將範本 (.zip) 檔案來*地區設定識別碼*資料夾。

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *地區設定識別碼*

     *YourTemplateName*.zip

     例如，如果您擁有名為 ContosoCustomAction.zip 支援英文 （美國） 地區設定的項目範本，可能是完整的路徑*ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*。

3. 在 **方案總管**，選擇的範本檔案 (*YourTemplateName*.zip)。

4. 在 **屬性**視窗中，將**建置動作**屬性設**內容**。

5. 開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇**開啟**。

     在設計工具中，開啟檔案。

6. 在 **資產**區段的編輯器中，選擇**新增**按鈕。

     **加入新資產**對話方塊隨即開啟。

7. 在 **型別**清單中，選擇**Microsoft.VisualStudio.ItemTemplate**或是**Microsoft.VisualStudio.ProjectTemplate**。

8. 在 **來源**清單中，選擇**檔案系統上的**。

9. 在**路徑**欄位中，輸入組件的完整路徑 (例如*ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*，或使用**瀏覽**按鈕來尋找和選擇組件，然後選擇**確定**  按鈕。

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>包含專案範本或項目範本的精靈

1. 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後再選擇**開啟**。

     在設計工具中，開啟檔案。

2. 在 **資產**區段的編輯器中，選擇**新增**按鈕。

     **加入新資產**對話方塊隨即開啟。

3. 在 **型別**清單中，選擇**Microsoft.VisualStudio.Assembly**。

4. 在 **來源**清單中，執行下列步驟：

    - 如果精靈組件是從專案和 VSIX 專案相同的方案中，選擇**目前的方案中的專案**。 在 **專案**清單中，選擇專案的名稱。

    - 如果精靈組件包含為您的專案中的檔案，請選擇**檔案系統上的**。 在 **路徑**欄位，輸入完整路徑到組件檔案，或使用**瀏覽**按鈕，以找出並選擇 組件。

5. 選擇 [確定]  按鈕。

### <a name="related-walkthroughs"></a>相關的逐步解說

下表列出的逐步解說，示範如何使用 VSIX 專案來部署不同類型的 SharePoint 工具擴充功能。

|擴充功能類型|相關的逐步解說|
|--------------------|--------------------------|
|延伸模組，其中包含延伸模組組件|[逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [逐步解說：建立 SharePoint 專案延伸模組](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [逐步解說：呼叫 SharePoint 用戶端物件模型，在 伺服器總管延伸模組](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|擴充功能，包括 SharePoint 命令|[逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [逐步解說：使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|擴充功能，包括 Visual Studio 範本|[逐步解說：使用項目範本，第 1 部分中建立自訂動作專案項目](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [逐步解說：使用專案範本，第 1 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|包含在範本精靈擴充功能|[逐步解說：建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [逐步解說：使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>手動建立 VSIX 封裝

如果您想要手動建立 VSIX 封裝，您的 SharePoint 工具擴充功能，請執行下列步驟：

1. 新的資料夾中建立 extension.vsixmanifest 檔案和 [Content_Types].xml 檔案。 如需詳細資訊，請參閱 < [VSIX 封裝的結構](../extensibility/anatomy-of-a-vsix-package.md)。

2. 在 Windows 檔案總管中，包含兩個 XML 檔案的資料夾上按一下滑鼠右鍵、 按一下 [傳送到]，然後按一下壓縮的 (zipped) 資料夾。 將產生的.zip 檔案的重新命名為 Filename.vsix，其中 Filename 是可轉散發檔案安裝封裝的名稱。

3. 將您的延伸模組組件新增至 VSIX 封裝中。 如果您的延伸模組包含 SharePoint 命令，也會新增實作 SharePoint 命令加入 VSIX 封裝的組件。

4. 修改 extension.vsixmanifest 檔案：

    - 新增`Microsoft.VisualStudio.MefComponent`項目底下`Assets`項目，然後再將設定要在 VSIX 封裝中實作您的延伸模組的組件的相對路徑的新項目值。 如需詳細資訊，請參閱 < [MEFComponent 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

    - 如果您的延伸模組包含可呼叫伺服器物件模型，適用於 SharePoint 的 SharePoint 命令，新增`Microsoft.VisualStudio.Assembly`項目底下`Assets`項目。 新項目的值設成 VSIX 封裝中實作之 SharePoint 命令的組件的相對路徑。 如需詳細資訊，請參閱 <<c0> [ 資產項目 （VSX 結構描述）](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)。

    - 如果您的延伸模組包含專案範本或項目範本，將`ProjectTemplate`或是`ItemTemplate`下方的項目`Assets`項目。 新項目的值設為包含在 VSIX 套件中的範本的資料夾的相對路徑。 如需詳細資訊，請參閱 < [ProjectTemplate 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\))並[ItemTemplate 項目 （VSX 結構描述）](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))。

    - 如果您的延伸模組包含專案範本或項目範本的自訂精靈，加入`Assembly`項目底下`Assets`項目。 將新項目的值設定為在 VSIX 封裝中，組件的相對路徑，然後設定`AssemblyName`屬性 （包括版本、 文化特性和公開金鑰語彙基元） 的完整組件名稱。 如需詳細資訊，請參閱 <<c0> [ 相依性項目 （VSX 結構描述）](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37)。

### <a name="example"></a>範例

下列範例顯示 SharePoint 工具擴充功能的 extension.vsixmanifest 檔案的內容。 延伸模組的實作，稱為 Contoso.ProjectExtension.dll 組件中。 擴充功能包含 SharePoint 命令組件 Contoso.ExtensionCommands.dll 和項目範本名為的資料夾下名為**項目範本**VSIX 封裝中。 這個範例假設這兩個組件位於 extension.vsixmanifest 檔案，在 VSIX 封裝相同的資料夾。

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>另請參閱

- [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)
- [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [偵錯在 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
