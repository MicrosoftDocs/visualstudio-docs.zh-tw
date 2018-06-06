---
title: 部署的 Visual Studio 中的 SharePoint 工具擴充功能 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dba88bde834ddf8e5eba938325b21434560827a1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767256"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>部署 Visual Studio 中 SharePoint 工具擴充功能
  若要部署的 SharePoint 工具擴充功能，建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝，其中包含延伸模組組件和任何其他您想要發佈副檔名的檔案。 VSIX 封裝是壓縮的檔案，會遵循開放封裝慣例 (OPC) 標準。 VSIX 封裝 *.vsix*延伸模組。  
  
 建立 VSIX 封裝之後，其他使用者可以執行.vsix 檔案來安裝您的擴充功能。 當使用者安裝您的擴充功能時，所有的檔案會安裝 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions 資料夾。 若要部署擴充功能，您可以上傳 VSIX 封裝，來[Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站上，或者您可以將套件發佈給您的客戶透過其他方式，例如所裝載的網路共用或某些其他網站上的套件。  
  
 如需有關建立 VSIX 封裝及部署他們[Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)，請參閱[傳送 Visual Studio 擴充功能](/visualstudio/extensibility/shipping-visual-studio-extensions)。  
  
 您可以建立 VSIX 封裝使用**VSIX 專案**範本在 Visual Studio 中，或者您可以手動建立 VSIX 封裝。  
  
## <a name="use-vsix-projects-to-create-vsix-packages"></a>使用 VSIX 專案建立 VSIX 封裝
 您可以使用**VSIX 專案**Visual Studio SDK，可以建立 VSIX 封裝，針對 SharePoint 工具擴充功能所提供的範本。 使用 VSIX 專案透過手動建立 VSIX 封裝，提供多項優點：  
  
-   當您建置專案時，visual Studio 會自動產生 VSIX 封裝。 為您完成工作，例如部署檔案新增至封裝，以及建立封裝的 [Content_Types].xml 檔案。  
  
-   您可以設定要在 VSIX 封裝中包含擴充功能專案和其他檔案，例如專案範本和項目範本的建置輸出 VSIX 專案。  
  
 如需有關如何使用 VSIX 專案的詳細資訊，請參閱[VSIX 專案範本](/visualstudio/extensibility/vsix-project-template)。  
  
### <a name="organize-your-projects"></a>組織您的專案
 根據預設，VSIX 專案只會產生 VSIX 封裝，而不是組件。 因此，您通常不會實作 SharePoint 工具擴充功能 VSIX 專案。 您通常會使用至少兩個專案：  
  
-   VSIX 專案。  
  
-   實作您的擴充功能的類別庫專案。  
  
 您可能也使用的其他專案特定類型的擴充功能：  
  
-   實作您的延伸模組所使用的任何 SharePoint 指令的類別庫專案。 如需示範此案例中的逐步解說，請參閱[逐步解說： 擴充伺服器總管 來顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)。  
  
-   如果您的延伸模組會定義新的 SharePoint 專案項目類型建立項目範本或專案範本的項目範本或專案範本專案。 如需示範此案例中的逐步解說，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
-   如果您的擴充功能隨附的範本，實作自訂精靈的項目範本、 專案範本的類別庫專案。 如需示範此案例中的逐步解說，請參閱[逐步解說： 建立自訂動作專案項目與項目範本，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)。  
  
 如果您在相同的 Visual Studio 方案中包含的所有專案，您可以修改 source.extension.vsixmanifest 檔案中包含組建輸出的類別庫專案在 VSIX 專案。  
  
### <a name="edit-the-vsix-manifest"></a>編輯 VSIX 資訊清單
 您必須編輯 source.extension.vsixmanifest 檔案中要包含您想要在您的擴充功能中包含的所有項目的項目在 VSIX 專案。 當您從快顯功能表開啟 source.extension.vsixmanifest 檔案時，檔案會顯示在設計工具中，提供用於編輯 XML 檔案中的 UI。 如需詳細資訊，請參閱[VSIX 資訊清單設計工具](/visualstudio/extensibility/vsix-manifest-designer)。  
  
 您必須為下列項目 source.extension.vsixmanifest 檔案中新增項目：  
  
-   延伸模組組件中。  
  
-   實作您的延伸模組所使用的任何 SharePoint 指令的組件。  
  
-   任何專案範本或與您的延伸模組相關聯的項目範本。  
  
-   範本與您的延伸模組相關聯的自訂精靈。  
  
 下列程序說明如何將項目新增至的.vsixmanifest 檔案中，針對每一個項目。  
  
##### <a name="to-include-the-extension-assembly"></a>包含延伸模組組件  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇 **開啟**。  
  
     在設計工具中開啟檔案  
  
2.  上**資產** 索引標籤的 編輯器 中，選擇 **新增** 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
3.  在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
4.  在**來源**清單中，執行下列步驟：  
  
    -   如果延伸模組組件建置在相同 VSIX 專案的方案中的專案，選擇**目前方案中的專案**。 在**專案**清單中，選擇專案的名稱。  
  
    -   如果延伸模組組件包含為您的專案中的檔案，請選擇**檔案系統上的檔案**。 在**路徑**清單中，延伸模組組件檔案中，輸入完整路徑或使用**瀏覽**按鈕以找出並選取組件檔案。  
  
5.  選擇 [確定]  按鈕。  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>若要包含 SharePoint 命令組件  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇 [**開啟**] 按鈕。  
  
     在設計工具中，開啟檔案。  
  
2.  在**資產**> 一節的編輯器中，選擇 [**新增**] 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
3.  在**類型**方塊中，輸入**SharePoint.Commands.v4**。  
  
4.  在**來源**清單中，執行下列步驟：  
  
    -   如果命令組件建置在相同 VSIX 專案的方案中的專案，選擇**目前方案中的專案**。 在**專案**清單中，選擇專案的名稱。  
  
    -   如果命令組件包含為您的專案中的檔案，請選擇**檔案系統上的檔案**。 在**路徑**清單中，延伸模組組件檔案中，輸入完整路徑或使用**瀏覽**按鈕以找出並選取組件檔案。  
  
5.  選擇 [確定]  按鈕。  
  
##### <a name="to-include-a-template-that-you-create"></a>要包含您所建立的範本  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇 [**開啟**] 按鈕。  
  
     在設計工具中，開啟檔案。  
  
2.  在**資產**> 一節的編輯器中，選擇 [**新增**] 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
3.  在**類型**清單中，選擇**Microsoft.VisualStudio.ProjectTemplate**或**Microsoft.VisualStudio.ItemTemplate**。  
  
4.  在**來源**清單中，選擇**目前方案中的專案**。  
  
5.  在**專案**清單中，選擇專案的名稱，然後選擇 [**確定**] 按鈕。  
  
6.  在**方案總管 中**，開啟您專案範本或項目範本專案的捷徑功能表，然後選擇**卸載專案**。  
  
7.  同樣地，開啟專案節點的捷徑功能表，然後選擇**編輯***YourTemplateProjectName***.csproj**或**編輯***YourTemplateProjectName***。vbproj**。  
  
8.  找出下列`VSTemplate`專案檔中的項目。  
  
    ```xml  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. 以下列 XML 取代此項目。  
  
    ```xml  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath`項目會指定其他資料夾中建置專案時，專案範本建立所在的路徑。 此處指定的資料夾確保項目範本會使用，只有當客戶**加入新的專案**對話方塊方塊中，展開  **SharePoint**  節點，然後選擇  **2010年**節點。  
  
10. 儲存並關閉檔案。  
  
11. 在**方案總管 中**，開啟專案範本或項目範本的專案的捷徑功能表，然後選擇**重新載入專案**。  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>要包含您手動建立的範本  
  
1.  在 VSIX 專案中，將新的資料夾加入專案以包含範本。  
  
2.  在這個新的資料夾底下建立下列資料夾中，並將範本 (.zip) 檔案*地區設定識別碼*資料夾。  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *地區設定識別碼*  
  
     *YourTemplateName*.zip  
  
     例如，如果您擁有名為 ContosoCustomAction.zip 支援英文 （美國） 地區設定的項目範本，可能是完整路徑*ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*。  
  
3.  在**方案總管 中**，選擇的範本檔案 (*YourTemplateName*.zip)。  
  
4.  在**屬性**視窗中，將**建置動作**屬性**內容**。  
  
5.  開啟 source.extension.vsixmanifest 檔案中的捷徑功能表，然後選擇**開啟**。  
  
     在設計工具中，開啟檔案。  
  
6.  在**資產**> 一節的編輯器中，選擇 [**新增**] 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
7.  在**類型**清單中，選擇**Microsoft.VisualStudio.ItemTemplate**或**Microsoft.VisualStudio.ProjectTemplate**。  
  
8.  在**來源**清單中，選擇**檔案系統上的檔案**。  
  
9. 在**路徑**欄位中，輸入組件的完整路徑 (例如， *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*，或使用**瀏覽**按鈕來找出並選擇組件，然後再選擇**確定** 按鈕。  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>包含專案範本或項目範本的精靈  
  
1.  在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，捷徑功能表，然後選擇 **開啟**。  
  
     在設計工具中，開啟檔案。  
  
2.  在**資產**> 一節的編輯器中，選擇 [**新增**] 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
3.  在**類型**清單中，選擇**Microsoft.VisualStudio.Assembly**。  
  
4.  在**來源**清單中，執行下列步驟：  
  
    -   如果精靈組件建置在相同 VSIX 專案的方案中的專案，選擇**目前方案中的專案**。 在**專案**清單中，選擇專案的名稱。  
  
    -   如果精靈組件包含為您的專案中的檔案，請選擇**檔案系統上的檔案**。 在**路徑**欄位中輸入完整路徑到組件檔案，或者使用**瀏覽**按鈕以找出並選取組件。  
  
5.  選擇 [確定]  按鈕。  
  
### <a name="related-walkthroughs"></a>相關的逐步解說
 下表列出逐步解說示範如何使用 VSIX 專案，才能部署不同類型的 SharePoint 工具擴充功能。  
  
|擴充功能類型|相關的逐步解說|  
|--------------------|--------------------------|  
|擴充功能，包括延伸模組組件|[逐步解說：擴充 SharePoint 專案項目類型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [逐步解說：建立 SharePoint 專案延伸模組](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [逐步解說：在伺服器總管延伸模組中呼叫 SharePoint 用戶端物件模型](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|擴充功能，包括 SharePoint 命令|[逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [逐步解說：擴充伺服器總管以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案項目 (第 2 部分)](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|擴充功能，包括 Visual Studio 範本|[逐步解說：使用項目範本建立自訂動作專案項目 (第 1 部分)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案項目 (第 1 部分)](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|包含的範本精靈擴充功能|[逐步解說：使用項目範本建立自訂動作專案項目 (第 2 部分)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [逐步解說：使用專案範本建立網站資料行專案項目 (第 2 部分)](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="create-vsix-packages-manually"></a>手動建立 VSIX 封裝
 如果您想要手動建立 VSIX 封裝，您的 SharePoint 工具擴充功能，請執行下列步驟：  
  
1.  Extension.vsixmanifest 檔案和 [Content_Types].xml 檔案在中建立新的資料夾。 如需詳細資訊，請參閱[VSIX 套件的剖析](/visualstudio/extensibility/anatomy-of-a-vsix-package)。  
  
2.  在 Windows 檔案總管] 中，以滑鼠右鍵按一下包含兩個 XML 檔案的資料夾、 按一下 [傳送到，然後按一下壓縮 (zipped) 資料夾。 重新產生的.zip 檔案命名為 Filename.vsix，其中 Filename 是可轉散發檔案安裝封裝的名稱。  
  
3.  將您的延伸模組組件加入至 VSIX 封裝。 如果您的擴充功能包含 SharePoint 命令，也新增實作 SharePoint 命令加入 VSIX 封裝組件。  
  
4.  修改 extension.vsixmanifest 檔案：  
  
    -   新增`Microsoft.VisualStudio.MefComponent`項目底下`Assets`項目，並將其設定的值要實作您的擴充功能 VSIX 封裝中的組件的相對路徑的新項目。 如需詳細資訊，請參閱[MEFComponent 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
    -   如果您的擴充功能包含 for SharePoint 伺服器物件模型呼叫 SharePoint 命令，新增`Microsoft.VisualStudio.Assembly`項目底下`Assets`項目。 新項目的值設為 VSIX 封裝中實作 SharePoint 命令的組件的相對路徑。 如需詳細資訊，請參閱[資產項目 （VSX 結構描述）](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737)。  
  
    -   如果您的擴充功能包含專案範本或項目範本，加入`ProjectTemplate`或`ItemTemplate`項目底下`Assets`項目。 新項目的值設為包含在 VSIX 封裝範本的資料夾的相對路徑。 如需詳細資訊，請參閱[ProjectTemplate 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)和[ItemTemplate 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0)。  
  
    -   如果您的擴充功能包含專案範本或項目範本的自訂精靈，加入`Assembly`項目底下`Assets`項目。 將新項目的值設定為 VSIX 封裝中的組件的相對路徑，然後設定`AssemblyName`屬性 （包括版本、 文化特性和公開金鑰語彙基元） 的完整組件名稱。 如需詳細資訊，請參閱[相依性項目 （VSX 結構描述）](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37)。  
  
### <a name="example"></a>範例  
 下列範例顯示 extension.vsixmanifest 檔案的 SharePoint 工具擴充功能的內容。 名為 Contoso.ProjectExtension.dll 的組件中實作的擴充功能。 擴充功能包含 SharePoint 命令組件 Contoso.ExtensionCommands.dll 和項目範本名為的資料夾下名為**ItemTemplates** VSIX 封裝中。 這個範例假設這兩個組件會為 extension.vsixmanifest 檔案，在 VSIX 封裝中的相同資料夾中。  
  
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
 [擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)   
 [擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [偵錯 Visual Studio 中 SharePoint 工具的延伸模組](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
