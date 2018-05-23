---
title: 逐步解說： 使用專案範本建立網站欄專案項目，第 1 部分 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f494ef7160d38365643f72cfd1dabfa6cb66d4c3
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1"></a>逐步解說：使用專案範本建立網站欄專案項目 (第 1 部分)
  SharePoint 專案的一或多個 SharePoint 專案項目的容器。 您可以擴充 SharePoint 專案系統，在 Visual Studio 中的建立您自己的 SharePoint 專案項目類型，然後將它們產生關聯的專案範本。 在本逐步解說中，您將建立網站資料行定義的專案項目類型，然後您將建立的專案範本，可用來建立新的專案，其中包含網站欄專案項目。  
  
 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能，可定義新的網站資料行的 SharePoint 專案項目類型。 專案項目類型包括簡單的自訂屬性會出現在**屬性**視窗。  
  
-   建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案範本的專案項目。  
  
-   建置[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]擴充功能 (VSIX) 封裝來部署專案範本和延伸模組組件。  
  
-   偵錯和測試專案項目。  
  
 這是獨立的逐步解說。 完成此逐步解說之後，您可以將精靈加入專案範本來增強專案項目。 如需詳細資訊，請參閱[逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
> [!NOTE]  
>  您可以下載範例，其中包含已完成的專案、 程式碼和其他檔案對於此逐步解說，請從下列位置： [ http://go.microsoft.com/fwlink/?LinkId=191369 ](http://go.microsoft.com/fwlink/?LinkId=191369)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說在開發電腦上：  
  
-   支援的版本的 Microsoft Windows，SharePoint 和[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱[開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說使用**VSIX 專案**SDK，以建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱[擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 下列概念的知識會很有幫助，但並非必要，完成此逐步解說：  
  
-   在 SharePoint 中的網站資料行。 如需詳細資訊，請參閱[資料行](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
-   Visual Studio 中的專案範本。 如需詳細資訊，請參閱[建立專案和項目範本](/visualstudio/ide/creating-project-and-item-templates)。  
  
## <a name="creating-the-projects"></a>建立專案  
 若要完成此逐步解說，您需要建立三個專案：  
  
-   VSIX 專案。 此專案會建立 VSIX 封裝來部署網站欄專案項目和專案範本。  
  
-   專案範本專案。 此專案會建立的專案範本，可用來建立新的 SharePoint 專案，其中包含網站欄專案項目。  
  
-   類別庫專案。 Visual Studio 擴充功能，定義行為的網站欄專案項目會實作這個專案。  
  
 開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
3.  在頂端**新專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。  
  
4.  展開**Visual Basic**或**Visual C#** 節點，然後選擇 **擴充性**節點。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
5.  在專案範本清單中選擇**VSIX 專案**。  
  
6.  在**名稱**方塊中，輸入**SiteColumnProjectItem**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**SiteColumnProjectItem**專案加入**方案總管 中**。  
  
#### <a name="to-create-the-project-template-project"></a>若要建立專案範本  
  
1.  在**方案總管] 中**，開啟 [解決方案] 節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在頂端**新專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。  
  
3.  展開**Visual C#** 或**Visual Basic** ] 節點，然後選擇 [**擴充性**節點。  
  
4.  在專案範本清單中選擇**C# 專案範本**或**Visual Basic 專案範本**範本。  
  
5.  在**名稱**方塊中，輸入**SiteColumnProjectTemplate**，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**SiteColumnProjectTemplate**專案加入方案。  
  
6.  從專案刪除 Class1 的程式碼檔案。  
  
7.  如果您建立 Visual Basic 專案，也從專案刪除下列檔案：  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  在**方案總管] 中**，開啟 [解決方案] 節點的捷徑功能表，選擇**新增**，然後選擇 [**新專案**。  
  
2.  在頂端**新專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。  
  
3.  展開**Visual C#** 或**Visual Basic**節點，並選擇**Windows** ] 節點，然後選擇 [**類別庫**範本。  
  
4.  在**名稱**方塊中，輸入**ProjectItemTypeDefinition** ，然後選擇 [**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ProjectItemTypeDefinition**專案加入方案，並開啟預設 Class1 的程式碼檔。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configuring-the-extension-project"></a>設定擴充功能專案  
 加入程式碼檔案和設定擴充功能專案中的組件參考。  
  
#### <a name="to-configure-the-project"></a>若要設定專案  
  
1.  在 ProjectItemTypeDefinition 專案，加入名為的程式碼檔案**SiteColumnProjectItemTypeProvider**。  
  
2.  在功能表列上，依序選擇 [專案] 和 [加入參考]。  
  
3.  在**參考管理員-ProjectItemTypeDefinition**對話方塊方塊中，展開 [**組件**] 節點，選擇**Framework**節點，然後再選取System.ComponentModel.Composition 核取方塊。  
  
4.  選擇**延伸** 節點，選取 Microsoft.VisualStudio.SharePoint 組件旁邊的核取方塊，然後選擇**確定** 按鈕。  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>定義新的 SharePoint 專案項目類型  
 建立類別，實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面來定義新的專案項目類型的行為。 每當您想要定義新的專案項目類型時，請實作這個介面。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>若要定義新的 SharePoint 專案項目類型  
  
1.  在**SiteColumnProjectItemTypeProvider**程式碼檔案，以下列程式碼，取代預設程式碼並儲存檔案。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="creating-a-visual-studio-project-template"></a>建立 Visual Studio 專案範本  
 藉由建立專案範本，您可以啟用其他開發人員建立網站欄專案項目所含的 SharePoint 專案。 SharePoint 專案範本包含所需的所有專案在 Visual Studio 中，例如.csproj 或.vbproj 和.vstemplate 檔案和檔案的 SharePoint 專案特定的檔案。 如需詳細資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 在此程序，您可以建立空白的 SharePoint 專案來產生 SharePoint 專案特定的檔案。 您再將這些檔案加入 SiteColumnProjectTemplate 專案，如此，它們是從這個專案會產生的範本。 您也可以設定 SiteColumnProjectTemplate 專案檔，以指定的專案範本出現在**新專案** 對話方塊。  
  
#### <a name="to-create-the-files-for-the-project-template"></a>若要建立專案範本的檔案  
  
1.  開始的第二個執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有系統管理認證。  
  
2.  建立名為 SharePoint 2010 專案**BaseSharePointProject**。  
  
    > [!IMPORTANT]  
    >  在**SharePoint 自訂精靈**，不要選取**部署為伺服陣列方案**選項按鈕。  
  
3.  空白項目項目加入專案，然後項目**Field1**。  
  
4.  儲存專案，然後關閉 第二個執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
5.  執行個體中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]在具有 SiteColumnProjectItem 方案開啟、**方案總管] 中**，開啟捷徑功能表**SiteColumnProjectTemplate**專案節點、 選擇**新增**，然後選擇 [**現有項目**。  
  
6.  在**加入現有項目**對話方塊中，開啟檔案的副檔名清單，然後選擇**所有檔案 (\*。\*)**.  
  
7.  在包含 BaseSharePointProject 專案目錄中，選取 key.snk 檔案，然後選擇**新增** 按鈕。  
  
    > [!NOTE]  
    >  在本逐步解說中，您所建立的專案範本會使用相同的 key.snk 檔案簽署使用範本建立的每個專案。 若要深入了解如何擴充這個範例，以建立不同的 key.snk 檔案以供每個專案的執行個體，請參閱[逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
8.  重複步驟 5 至 8 BaseSharePointProject 目錄中指定的子資料夾將下列檔案：  
  
    -   \Field1\Elements.xml  
  
    -   \Field1\SharePointProjectItem.spdata  
  
    -   \Features\Feature1\Feature1.feature  
  
    -   \Features\Feature1\Feature1.Template.xml  
  
    -   \Package\Package.package  
  
    -   \Package\Package.Template.xml  
  
     將這些檔案直接加入 SiteColumnProjectTemplate 專案;不重新建立專案中的 Field1、 功能或封裝的子資料夾。 如需有關這些檔案的詳細資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>若要設定開發人員如何探索新的專案 對話方塊中的專案範本  
  
1.  在**方案總管 中**，開啟捷徑功能表**SiteColumnProjectTemplate**專案節點，然後選擇**卸載專案**。 如果提示您將變更儲存至任何檔案時，請選擇**是** 按鈕。  
  
2.  開啟快顯功能表**SiteColumnProjectTemplate**節點，然後選擇 **編輯 SiteColumnProjectTemplate.csproj**或**編輯 SiteColumnProjectTemplate.vbproj**.  
  
3.  在專案檔中，找出下列`VSTemplate`項目。  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  以下列 XML 取代此項目。  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath`項目會指定其他資料夾中建置專案時，專案範本建立所在的路徑。 此處指定的資料夾，確保專案範本會可用，只有當客戶**新專案**對話方塊方塊中，展開  **SharePoint**  節點，然後選擇  **2010年**節點。  
  
5.  儲存並關閉檔案。  
  
6.  在**方案總管 中**，開啟捷徑功能表**SiteColumnProjectTemplate**專案，然後再選擇**重新載入專案**。  
  
## <a name="editing-the-project-template-files"></a>編輯專案範本檔案  
 在 SiteColumnProjectTemplate 專案中，編輯下列檔案，以定義專案範本的行為：  
  
-   AssemblyInfo.cs 或 AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   中  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj 或 ProjectTemplate.vbproj  
  
 在下列程序中，您會加入至這當中有些檔案的可置換的參數。 可取代的參數是權杖的開始和結束都貨幣符號 （$） 字元。 當使用者使用這個專案範本建立專案時，Visual Studio 會自動取代新的專案中的這些參數具有特定值。 如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>若要編輯的 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，開啟 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案，並將加入下列陳述式的頂端：  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     當**沙箱化方案**SharePoint 專案的屬性設定為**True**，Visual Studio 會加入<xref:System.Security.AllowPartiallyTrustedCallersAttribute>AssemblyInfo 程式碼檔案。 不過，不會匯入 AssemblyInfo 程式碼檔案中的專案範本<xref:System.Security>預設命名空間。 您必須將這個加入**使用**或**匯入**陳述式，以避免編譯錯誤。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-elementsxml-file"></a>若要編輯的 Elements.xml 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，請以下列 XML 取代 Elements.xml 檔案的內容。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     加入新的 XML`Field`定義的網站資料行、 其基底類型和要列出網站中的資料行組件庫中的群組名稱的項目。 這個檔案的內容的相關資訊，請參閱[欄位定義結構描述](http://go.microsoft.com/fwlink/?LinkId=184290)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>若要編輯 SharePointProjectItem.spdata 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，請以下列 XML 取代 SharePointProjectItem.spdata 檔案的內容。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     新的 XML 會對檔案進行下列變更：  
  
    -   變更`Type`屬性`ProjectItem`項目相同的字串傳遞至<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>專案項目定義上 (`SiteColumnProjectItemTypeProvider`您稍早在本逐步解說中建立的類別)。  
  
    -   移除`SupportedTrustLevels`和`SupportedDeploymentScopes`屬性從`ProjectItem`項目。 這些屬性的值是不必要的因為在指定的信任層級和部署範圍`SiteColumnProjectItemTypeProvider`ProjectItemTypeDefinition 專案中的類別。  
  
     .Spdata 檔案的內容的相關資訊，請參閱[SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-feature1feature-file"></a>若要編輯 Feature1.feature 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，請以下列 XML 取代 Feature1.feature 檔案的內容。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     新的 XML 會對檔案進行下列變更：  
  
    -   值變更`Id`和`featureId`屬性`feature`元素`$guid4$`。  
  
    -   值變更`itemId`屬性`projectItemReference`元素`$guid2$`。  
  
     如需.feature 檔案的詳細資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-packagepackage-file"></a>若要編輯 Package.package 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，請以下列 XML 取代 Package.package 檔案的內容。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     新的 XML 會對檔案進行下列變更：  
  
    -   值變更`Id`和`solutionId`屬性`package`元素`$guid3$`。  
  
    -   值變更`itemId`屬性`featureReference`元素`$guid4$`。  
  
     如需.package 檔案的詳細資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>若要編輯 SiteColumnProjectTemplate.vstemplate 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，取代 SiteColumnProjectTemplate.vstemplate 檔案的內容的下列區段的 XML。  
  
    -   如果您要建立 Visual C# 專案範本，請使用下列 XML。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   如果您要建立 Visual Basic 專案範本，請使用下列 XML。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     新的 XML 會對檔案進行下列變更：  
  
    -   設定`Name`值的項目**網站資料行**。 (這個名稱會出現在**新專案**對話方塊)。  
  
    -   新增`ProjectItem`filethat 每個元素的包含在每個專案的執行個體。  
  
    -   使用命名空間"http://schemas.microsoft.com/developer/vstemplate/2005"。 其他專案檔案，在此解決方案使用 「http://schemas.microsoft.com/developer/msbuild/2003"命名空間。 因此，將會產生 XML 結構描述警告訊息，但是您可以忽略這些在本逐步解說。  
  
     這個.vstemplate 檔案的內容的相關資訊，請參閱[Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>若要編輯的 ProjectTemplate.csproj 或 ProjectTemplate.vbproj 檔案  
  
1.  在 SiteColumnProjectTemplate 專案中，取代 ProjectTemplate.csproj 檔案或 ProjectTemplate.vbproj 檔案的內容的下列區段的 XML。  
  
    -   如果您要建立 Visual C# 專案範本，請使用下列 XML。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  如果您要建立 Visual Basic 專案範本，請使用下列 XML。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     新的 XML 會對檔案進行下列變更：  
  
    -   使用`TargetFrameworkVersion`項目來指定.NET Framework 3.5，而非 4.5。  
  
    -   新增`SignAssembly`和`AssemblyOriginatorKeyFile`来簽署專案輸出項目。  
  
    -   新增`Reference`的組件元素參考 SharePoint 專案使用。  
  
    -   在專案中，例如 Elements.xml 和 SharePointProjectItem.spdata 加入每個預設檔案的項目。  
  
2.  儲存並關閉檔案。  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-template"></a>建立 VSIX 封裝，來部署專案範本  
 若要部署擴充功能，使用中的 VSIX 專案**SiteColumnProjectItem**方案以建立 VSIX 封裝。 首先，設定 VSIX 封裝，藉由修改 source.extension.vsixmanifest 檔案中包含在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定，並建立 VSIX 封裝  
  
1.  在**方案總管 中**，請在**SiteColumnProjectItem**專案中，資訊清單編輯器 中，開啟 source.extension.vsixmanifest 檔案。  
  
     Source.extension.vsixmanifest 檔案是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱[VSIX 擴充功能結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在**產品名稱**方塊中，輸入**網站資料行**。  
  
3.  在**作者**方塊中，輸入**Contoso**。  
  
4.  在**描述**方塊中，輸入**用來建立網站資料行的 SharePoint 專案**。  
  
5.  選擇**資產**索引標籤，然後選擇 [**新增**] 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
6.  在**類型**清單中，選擇**Microsoft.VisualStudio.ProjectTemplate**。  
  
    > [!NOTE]  
    >  這個值會對應到`ProjectTemplate`extension.vsixmanifest 檔案中的項目。 此項目會識別的子資料夾中包含的專案範本的 VSIX 套件。 如需詳細資訊，請參閱[ProjectTemplate 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)。  
  
7.  在**來源**清單中，選擇**目前方案中的專案**。  
  
8.  在**專案**清單，並選擇**SiteColumnProjectTemplate**，然後選擇 [**確定**] 按鈕。  
  
9. 選擇**新增**按鈕一次。  
  
     **加入新資產**對話方塊隨即開啟。  
  
10. 在**類型**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個項目 VSIX 封裝中指定延伸模組組件的名稱。 如需詳細資訊，請參閱[MEFComponent 元素 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在**來源**清單中，選擇**目前方案中的專案**。  
  
12. 在**專案**清單中，選擇**ProjectItemTypeDefinition**，然後選擇 [**確定**] 按鈕。  
  
13. 在功能表列上選擇 **建置**，**建置方案**，然後確認專案編譯無誤。  
  
## <a name="testing-the-project-template"></a>測試專案範本  
 現在您已經準備好進行測試的專案範本。 首先，開始偵錯 SiteColumnProjectItem 方案在 Visual Studio 的實驗執行個體。 然後，測試**網站資料行**Visual Studio 的實驗執行個體中的專案。 最後，建置並執行 SharePoint 專案，以確認站台的資料行可以正常運作。  
  
#### <a name="to-start-debugging-the-solution"></a>若要啟動偵錯方案  
  
1.  系統管理認證，以重新啟動 Visual Studio，然後開啟 SiteColumnProjectItem 方案。  
  
2.  
  
3.  在 SiteColumnProjectItemTypeProvider 程式碼檔案中，將中斷點加入至程式碼中的第一行`InitializeType`方法，然後選擇  **F5**鍵開始偵錯。  
  
     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 來安裝擴充功能，並啟動 Visual studio 的實驗執行個體。 您將這個執行個體的 Visual Studio 中測試的專案項目。  
  
#### <a name="to-test-the-project-in-visual-studio"></a>在 Visual Studio 測試專案  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**檔案**，**新增**，**專案**。  
  
2.  展開**Visual C#** 或**Visual Basic**節點 （取決於您的專案範本支援語言），依序展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
3.  在專案範本清單中選擇**網站資料行**範本。  
  
4.  在**名稱**方塊中，輸入**SiteColumnTest** ，然後選擇 [**確定**] 按鈕。  
  
     在**方案總管 中**，新的專案隨即出現，並命名為專案項目**Field1**。  
  
5.  確認 Visual Studio 的其他執行個體中的程式碼是您稍早在設定的中斷點上停止`InitializeType`方法，然後選擇  **F5**鍵繼續偵錯專案。  
  
6.  在**方案總管 中**，選擇**Field1**  節點，然後選擇  **F4**索引鍵。  
  
     **屬性**視窗隨即開啟。  
  
7.  在 [屬性] 清單中，確認屬性**範例屬性**隨即出現。  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>若要在 SharePoint 中測試網站資料行  
  
1.  在**方案總管 中**，選擇**SiteColumnTest**節點。  
  
2.  在**屬性**視窗中，旁邊的文字方塊中**網站 URL**屬性中，輸入**http://localhost**。  
  
     此步驟會指定您想要用於偵錯在開發電腦上之本機 SharePoint 網站。  
  
    > [!NOTE]  
    >  **網站 URL**屬性預設是空的網站資料行專案範本並不提供精靈來建立專案時，收集此值。 若要了解如何加入精靈，這個值會要求開發人員，並接著在新的專案中設定這個屬性，請參閱[逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
3.  選擇 **F5** 鍵。  
  
     封裝和部署到 SharePoint 網站中所指定的站台的資料行**網站 URL**專案的屬性。 網頁瀏覽器會開啟此站台的預設頁面。  
  
    > [!NOTE]  
    >  如果**指令碼偵錯已停用**對話方塊出現時，選擇 **是**按鈕以繼續進行偵錯專案。  
  
4.  在**網站動作**功能表上，選擇**站台設定**。  
  
5.  在**站台設定**頁面的 **圖庫**清單中，選擇**站台的資料行**連結。  
  
6.  在站台的資料行清單中，確認**自訂資料行**群組包含資料行名為**SiteColumnTest**。  
  
7.  關閉網頁瀏覽器。  
  
## <a name="cleaning-up-the-development-computer"></a>清除開發電腦  
 完成測試專案之後，請從 Visual Studio 的實驗執行個體中移除專案範本。  
  
#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦  
  
1.  在功能表列上的 Visual Studio 實驗執行個體選擇**工具**，**擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在擴充功能清單中，選擇 **網站資料行**延伸模組，然後選擇 **解除安裝** 按鈕。  
  
3.  在出現的對話方塊中，選擇 **是**按鈕，以確認您想要解除安裝擴充功能。  
  
4.  選擇**關閉**按鈕，以完成解除安裝。  
  
5.  關閉 Visual Studio （實驗性執行個體和 SiteColumnProjectItem 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。  
  
## <a name="next-steps"></a>後續步驟  
 完成此逐步解說之後，精靈可以加入的專案範本。 當使用者建立網站欄專案時，精靈會要求使用者輸入要用於偵錯，以及是否沙箱，新方案的網站 URL 和精靈設定新的專案，這項資訊。 精靈也會收集的資料行 （例如基底類型和要列出站台的資料行組件庫中的資料行中的群組） 的相關資訊，並將這項資訊加入至新的專案中的 Elements.xml 檔案。 如需詳細資訊，請參閱[逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 使用專案範本，第 2 部分建立網站欄專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [建立項目範本和專案範本的 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [擴充 SharePoint 專案系統中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [讓自訂資料與 SharePoint 工具延伸模組產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  