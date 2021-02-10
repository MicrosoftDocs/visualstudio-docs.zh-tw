---
title: 在 Visual Studio 中部署 SharePoint 工具的延伸模組 |Microsoft Docs
description: 在 Visual Studio 中部署 SharePoint 工具的擴充功能。 使用 Visual Studio 擴充功能 (VSIX) 專案來建立 VSIX 套件。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6a899bcc132b9229c1046dee5793278f79ea9e5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948891"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>在 Visual Studio 中部署 SharePoint 工具的延伸模組

若要部署 SharePoint tools 擴充功能，請建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含擴充元件的擴充功能 (VSIX) 封裝，以及您想要使用擴充功能散發的任何其他檔案。 VSIX 封裝是遵循開放式封裝慣例 (OPC) 標準的壓縮檔案。 VSIX 封裝的副檔名為 *.vsix* 。

建立 VSIX 封裝之後，其他使用者就可以執行 .vsix 檔來安裝您的延伸模組。 當使用者安裝您的延伸模組時，所有檔案都會安裝到%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions 資料夾。 若要部署擴充功能，您可以將 VSIX 封裝上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 網站，也可以透過其他方式將封裝散發給您的客戶，例如在網路共用或其他網站上裝載套件。

如需建立 VSIX 套件並將其部署至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)的詳細資訊，請參閱 [運送 Visual Studio 擴充](../extensibility/shipping-visual-studio-extensions.md)功能。

 您可以使用 Visual Studio 中的 **Vsix 專案** 範本建立 vsix 封裝，也可以手動建立 vsix 套件。

## <a name="use-vsix-projects-to-create-vsix-packages"></a>使用 VSIX 專案建立 VSIX 套件

您可以使用 Visual Studio SDK 提供的 **Vsix 專案** 範本來建立適用于 SharePoint 工具擴充功能的 vsix 套件。 使用 VSIX 專案可提供數個優點，而不是手動建立 VSIX 套件：

- 當您建立專案時，Visual Studio 會自動產生 VSIX 套件。 您可以為您完成將部署檔案加入封裝，以及為套件建立 [Content_Types] .xml 檔案等工作。

- 您可以設定 VSIX 專案，在 VSIX 封裝中包含擴充功能專案和其他檔案（例如專案範本和專案範本）的組建輸出。

如需使用 VSIX 專案的詳細資訊，請參閱 [Vsix 專案範本](../extensibility/vsix-project-template.md)。

### <a name="organize-your-projects"></a>組織您的專案

根據預設，VSIX 專案只會產生 VSIX 封裝，而不會產生元件。 因此，您通常不會在 VSIX 專案中執行 SharePoint 工具延伸模組。 您通常會使用至少兩個專案：

- VSIX 專案。

- 執行延伸模組的類別庫專案。

您也可以針對特定類型的延伸模組使用其他專案：

- 類別庫專案，可執行您的延伸模組所使用的任何 SharePoint 命令。 如需示範此案例的逐步解說，請參閱 [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。

- 專案範本或專案範本專案，如果您的延伸模組定義了新的 SharePoint 專案專案類型，則會建立專案範本或專案範本。 如需示範此案例的逐步解說，請參閱 [逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。

- 如果您的延伸模組包含範本，則為專案範本或專案範本執行自訂 wizard 的類別庫專案。 如需示範此案例的逐步解說，請參閱 [逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。

如果您將所有專案包含在相同的 Visual Studio 方案中，您可以修改 VSIX 專案中的 extension.vsixmanifest 檔案，以包含類別庫專案的組建輸出。

### <a name="edit-the-vsix-manifest"></a>編輯 VSIX 資訊清單

您必須編輯 VSIX 專案中的 extension.vsixmanifest 檔案，以包含您要包含在延伸模組中之所有專案的專案。 當您從快捷方式功能表開啟 extension.vsixmanifest 檔案時，檔案會出現在設計工具中，以提供在檔案中編輯 XML 的 UI。 如需詳細資訊，請參閱 [VSIX 資訊清單設計](../extensibility/vsix-manifest-designer.md)工具。

您必須將專案加入至 extension.vsixmanifest 檔案中的下列專案：

- 延伸模組元件。

- 元件，該元件會執行您的延伸模組所使用的任何 SharePoint 命令。

- 與您的延伸模組相關聯的任何專案範本或專案範本。

- 與您的延伸模組相關聯之範本的自訂 wizard。

下列程式說明如何將專案加入至每個專案的 extension.vsixmanifest 檔案。

#### <a name="to-include-the-extension-assembly"></a>包含擴充元件

1. 在 VSIX 專案中，開啟 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     檔案會在設計工具中開啟

2. 在編輯器的 [ **資產** ] 索引標籤上，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

3. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. [microsoft.visualstudio.mefcomponent]**]。

4. 在 [ **來源** ] 清單中，執行下列其中一個步驟：

    - 如果擴充元件是從與 VSIX 專案相同方案中的專案所建立，請選擇 [ **目前方案] 中的專案**。 在 [ **專案** ] 清單中，選擇專案的名稱。

    - 如果延伸模組元件包含為專案中的檔案，請選擇 [ **檔案系統] 上** 的 [檔案]。 在 [ **路徑** ] 清單中，輸入擴充元件檔案的完整路徑，或使用 [ **流覽]** 按鈕來尋找並選擇元件檔案。

5. 選擇 [確定]  按鈕。

#### <a name="to-include-a-sharepoint-command-assembly"></a>包含 SharePoint 命令元件

1. 在 VSIX 專案中，開啟 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [ **開啟** ] 按鈕。

     檔案隨即在設計工具中開啟。

2. 在編輯器的 [ **資產** ] 區段中，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

3. 在 [ **類型** ] 方塊中，輸入 [ **v4**]。

4. 在 [ **來源** ] 清單中，執行下列其中一個步驟：

    - 如果命令元件是從與 VSIX 專案相同方案中的專案所建立，請選擇 [ **目前方案] 中的專案**。 在 [ **專案** ] 清單中，選擇專案的名稱。

    - 如果命令元件包含為專案中的檔案，請選擇 **檔案系統上** 的 [檔案]。 在 [ **路徑** ] 清單中，輸入擴充元件檔案的完整路徑，或使用 [ **流覽]** 按鈕來尋找並選擇元件檔案。

5. 選擇 [確定]  按鈕。

#### <a name="to-include-a-template-that-you-create"></a>包含您建立的範本

1. 在 VSIX 專案中，開啟 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [ **開啟** ] 按鈕。

     檔案隨即在設計工具中開啟。

2. 在編輯器的 [ **資產** ] 區段中，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

3. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio. ProjectTemplate** ] 或 [ **VisualStudio**]。

4. 在 [ **來源** ] 清單中，選擇 [ **目前方案中的專案**]。

5. 在 [ **專案** ] 清單中，選擇專案的名稱，然後選擇 [ **確定]** 按鈕。

6. 在 **方案總管** 中，開啟專案範本或專案範本專案的快捷方式功能表，然後選擇 **[卸載專案**]。

7. 再次開啟專案節點的快捷方式功能表，然後選擇 [ **編輯**_YourTemplateProjectName_**.Csproj** ] 或 [ **編輯**_YourTemplateProjectName_**. vbproj**]。

8. 在專案檔中找出下列 `VSTemplate` 元素。

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. 將此元素取代為下列 XML。

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`專案會在建立專案時，指定用來建立專案範本的路徑中的其他資料夾。 在這裡指定的資料夾可確保只有當客戶開啟 [ **加入新專案** ] 對話方塊、展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點時，才會提供專案範本。

10. 儲存並關閉檔案。

11. 在 **方案總管** 中，開啟專案範本或專案範本專案的快捷方式功能表，然後選擇 [ **重載專案**]。

#### <a name="to-include-a-template-that-you-create-manually"></a>包含您手動建立的範本

1. 在 VSIX 專案中，將新資料夾新增至專案以包含範本。

2. 在這個新資料夾底下建立下列子資料夾，然後將範本 ( .zip) 檔新增至 *地區設定識別碼* 資料夾。

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *地區設定識別碼*

     *YourTemplateName*.zip

     例如，如果您有一個名為 ContosoCustomAction.zip 的專案範本，且該範本支援英文 () 美國地區設定，則可能會 *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* 完整路徑。

3. 在 **方案總管** 中，選擇 (*YourTemplateName*.zip) 的範本檔案。

4. 在 [ **屬性** ] 視窗中，將 [ **組建動作** ] 屬性設定為 [ **內容**]。

5. 開啟 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     檔案隨即在設計工具中開啟。

6. 在編輯器的 [ **資產** ] 區段中，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

7. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio** ] 或 [ **VisualStudio. ProjectTemplate**]。

8. 在 [ **來源** ] 清單中，選擇 **檔案系統上** 的 [檔案]。

9. 在 [ **路徑** ] 欄位中，輸入元件的完整路徑 (例如 *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*，或使用 [ **流覽]** 按鈕來尋找並選擇元件，然後選擇 [ **確定]** 按鈕。

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>若要包含專案範本或專案範本的 wizard

1. 在 VSIX 專案中，開啟 extension.vsixmanifest 檔案的快捷方式功能表，然後選擇 [ **開啟**]。

     檔案隨即在設計工具中開啟。

2. 在編輯器的 [ **資產** ] 區段中，選擇 [ **新增** ] 按鈕。

     [ **加入新資產** ] 對話方塊隨即開啟。

3. 在 [ **類型** ] 清單中，選擇 [ **VisualStudio**]。

4. 在 [ **來源** ] 清單中，執行下列其中一個步驟：

    - 如果 wizard 元件是從與 VSIX 專案相同方案中的專案所建立，請選擇 [ **目前方案] 中的專案**。 在 [ **專案** ] 清單中，選擇專案的名稱。

    - 如果 wizard 元件包含為專案中的檔案，請選擇 **檔案系統上** 的 [檔案]。 在 [ **路徑** ] 欄位中，輸入元件檔案的完整路徑，或使用 [ **流覽]** 按鈕來尋找並選擇元件。

5. 選擇 [確定]  按鈕。

### <a name="related-walkthroughs"></a>相關逐步解說

下表列出的逐步解說會示範如何使用 VSIX 專案部署不同類型的 SharePoint 工具延伸模組。

|延伸模組類型|相關逐步解說|
|--------------------|--------------------------|
|只包含擴充元件的延伸模組|[逐步解說：擴充 SharePoint 專案專案類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [逐步解說：建立 SharePoint 專案延伸模組](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [逐步解說：在伺服器總管擴充功能中呼叫 SharePoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|包含 SharePoint 命令的延伸模組|[逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|包含 Visual Studio 範本的延伸模組|[逐步解說：使用專案範本建立自訂動作專案專案（第1部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案專案（第1部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|包含範本 wizard 的延伸模組|[逐步解說：使用專案範本建立自訂動作專案專案（第2部分）](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>手動建立 VSIX 封裝

如果您想要手動建立 SharePoint 工具擴充功能的 VSIX 封裝，請執行下列步驟：

1. 在新的資料夾中建立 extension.vsixmanifest 檔案和 [Content_Types] .xml 檔案。 如需詳細資訊，請參閱 [VSIX 封裝的剖析](../extensibility/anatomy-of-a-vsix-package.md)。

2. 在 Windows 檔案總管中，以滑鼠右鍵按一下包含這兩個 XML 檔案的資料夾，按一下 [傳送到]，然後按一下 [壓縮的 (壓縮) 資料夾]。 將產生的 .zip 檔案重新命名為檔案名稱.vsix，其中檔案名稱是安裝封裝的可轉散發檔案名稱。

3. 將您的擴充元件新增至 VSIX 套件。 如果您的延伸模組包含 SharePoint 命令，也請將可執行 SharePoint 命令的元件加入至 VSIX 套件。

4. 修改 extension.vsixmanifest 檔案：

    - 在專案底下加入專案 `Microsoft.VisualStudio.MefComponent` `Assets` ，然後將新元素的值設定為在 VSIX 封裝中執行延伸模組之元件的相對路徑。 如需詳細資訊，請參閱 [[Microsoft.visualstudio.mefcomponent] 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

    - 如果您的延伸模組包含一個 SharePoint 命令，其會呼叫 SharePoint 的伺服器物件模型，請在專案底下加入 `Microsoft.VisualStudio.Assembly` 元素 `Assets` 。 將新元素的值設定為在 VSIX 封裝中執行 SharePoint 命令的元件相對路徑。 如需詳細資訊，請參閱 [資產元素 (VSX 架構) ](/previous-versions/dd393737(v=vs.110))。

    - 如果您的延伸模組包含專案範本或專案範本，請 `ProjectTemplate` 在元素底下加入或專案 `ItemTemplate` `Assets` 。 將新專案的值設定為 VSIX 封裝中包含範本之資料夾的相對路徑。 如需詳細資訊，請參閱 [ProjectTemplate 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) 和 [ITEMTEMPLATE 元素 (VSX 架構) ](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))。

    - 如果您的延伸模組包含專案範本或專案範本的自訂嚮導，請在專案底下加入 `Assembly` 元素 `Assets` 。 將新專案的值設定為 VSIX 封裝中元件的相對路徑，然後將 `AssemblyName` 屬性設定為完整元件名稱 (包括版本、文化特性和公開金鑰 token) 。 如需詳細資訊，請參閱 [ (VSX 架構) ](/previous-versions/dd393682(v=vs.110))的相依性元素。

### <a name="example"></a>範例

下列範例會顯示 SharePoint 工具延伸模組的 extension.vsixmanifest 檔案內容。 擴充功能會在名為 Contoso.ProjectExtension.dll 的元件中執行。 延伸模組包含名為 Contoso.ExtensionCommands.dll 的 SharePoint 命令元件，以及 VSIX 封裝中名為 **ItemTemplates** 的資料夾下的專案範本。 這個範例假設兩個元件都在 VSIX 套件中的 extension.vsixmanifest 檔案所在的同一個資料夾中。

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
- [擴充伺服器總管中的 [SharePoint 連接] 節點](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Visual Studio 中 SharePoint 工具的 Debug 擴充功能](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)