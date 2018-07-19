---
title: 逐步解說： 使用專案範本建立網站資料行專案項目，第 1 部分 |Microsoft Docs
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
ms.openlocfilehash: 3d34c03d74aae6ba1fb82e7357b6159b261cc2ad
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118635"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>逐步解說： 使用專案範本，第 1 部分中建立網站資料行專案項目
  SharePoint 專案的一或多個 SharePoint 專案項目的容器。 您可以擴充 SharePoint 專案系統，在 Visual Studio 中的建立您自己的 SharePoint 專案項目類型，然後再將它們關聯的專案範本。 在本逐步解說中，您將建立網站資料行定義的專案項目類型，然後會建立專案範本，可用來建立新的專案，其中包含網站資料行專案項目。  
  
 本逐步解說將示範下列工作：  
  
-   建立 Visual Studio 擴充功能定義新類型的網站資料行的 SharePoint 專案項目。 專案項目類型包含簡單的自訂屬性中會出現**屬性**視窗。  
  
-   建立[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]專案項目的專案範本。  
  
-   建置[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]来部署的專案範本和延伸模組組件的擴充功能 (VSIX) 封裝。  
  
-   偵錯和測試的專案項目。  
  
 這是獨立的逐步解說。 完成此逐步解說後，您可以增強的專案項目加入專案範本的精靈。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
> [!NOTE]  
> 針對一系列的範例工作流程中，請參閱[SharePoint 工作流程範例](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要完成這個逐步解說在開發電腦上的下列元件：  
  
-   支援版本的 Microsoft Windows、 SharePoint 和[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說會使用**VSIX 專案**SDK 來建立 VSIX 封裝，來部署專案項目中的範本。 如需詳細資訊，請參閱 <<c0> [ 擴充 Visual Studio 中 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。  
  
 下列概念的知識會很有幫助，但並非必要，若要完成本逐步解說：  
  
-   在 SharePoint 中的網站資料行。 如需詳細資訊，請參閱 <<c0> [ 資料行](http://go.microsoft.com/fwlink/?LinkId=183547)。  
  
-   Visual Studio 中的專案範本。 如需詳細資訊，請參閱[建立專案和項目範本](/visualstudio/ide/creating-project-and-item-templates)。  
  
## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說中，您需要建立三個專案：  
  
-   VSIX 專案。 此專案建立 VSIX 封裝來部署網站資料行專案項目和專案範本。  
  
-   專案範本專案。 此專案會建立專案範本，可用來建立新的 SharePoint 專案所在的網站資料行專案項目。  
  
-   類別庫專案。 實作定義行為的網站資料行專案項目的 Visual Studio 擴充此專案。  
  
 開始本逐步解說建立的專案。  
  
#### <a name="to-create-the-vsix-project"></a>若要建立 VSIX 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在功能表列上，選擇 [檔案] > [新增] > [專案]。  
  
3.  在頂端**新的專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。  
  
4.  依序展開**Visual Basic**或是**Visual C#** 節點，然後選擇 **擴充性**節點。  
  
    > [!NOTE]  
    >  **擴充性**節點才會提供您安裝 Visual Studio SDK。 如需詳細資訊，請參閱稍早在本主題中的必要條件 > 一節。  
  
5.  在專案範本清單中，選擇**VSIX 專案**。  
  
6.  在 [**名稱**方塊中，輸入**SiteColumnProjectItem**，然後選擇 **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**SiteColumnProjectItem**專案加入**方案總管 中**。  
  
#### <a name="to-create-the-project-template-project"></a>若要建立專案範本專案  
  
1.  中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。  
  
2.  在頂端**新的專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。  
  
3.  依序展開**Visual C#** 或**Visual Basic**節點，然後選擇**擴充性**節點。  
  
4.  在專案範本清單中，選擇**C# 專案範本**或是**Visual Basic 專案範本**範本。  
  
5.  在 [**名稱**方塊中，輸入**SiteColumnProjectTemplate**，然後選擇 **[確定]** ] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**SiteColumnProjectTemplate**專案加入方案。  
  
6.  從專案刪除 Class1 的程式碼檔案。  
  
7.  如果您建立 Visual Basic 專案，也從專案刪除下列檔案：  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *Resources.resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.settings  
  
#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案  
  
1.  中**方案總管**，開啟方案節點的捷徑功能表，選擇**新增**，然後選擇**新專案**。  
  
2.  在頂端**新的專案**對話方塊方塊中，請確定 **.NET Framework 4.5**選擇清單中的.NET Framework 版本。  
  
3.  依序展開**Visual C#** 或**Visual Basic**節點，並選擇**Windows**  節點，然後選擇**類別庫**範本。  
  
4.  在 [**名稱**方塊中，輸入**ProjectItemTypeDefinition** ，然後選擇**確定**] 按鈕。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增**ProjectItemTypeDefinition**專案加入方案，並開啟預設 Class1 的程式碼檔案。  
  
5.  從專案刪除 Class1 的程式碼檔案。  
  
## <a name="configure-the-extension-project"></a>設定擴充功能專案
 新增程式碼檔案和設定擴充功能專案的組件參考。  
  
#### <a name="to-configure-the-project"></a>若要設定專案  
  
1.  在 ProjectItemTypeDefinition 專案中加入程式碼檔案，稱為**SiteColumnProjectItemTypeProvider**。  
  
2.  在功能表列上選擇 **專案** > **加入參考**。  
  
3.  在**參考管理員-ProjectItemTypeDefinition**對話方塊方塊中，展開**組件**節點，選擇**Framework**節點，，然後選取System.ComponentModel.Composition 核取方塊。  
  
4.  選擇**延伸模組**節點中，選取 Microsoft.VisualStudio.SharePoint 組件旁邊的核取方塊，然後選擇**確定** 按鈕。  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>定義新的 SharePoint 專案項目類型
 建立類別，實作<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>介面來定義新的專案項目類型的行為。 每當您想要定義新類型的專案項目時，請實作這個介面。  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>若要定義新的 SharePoint 專案項目類型  
  
1.  在  **SiteColumnProjectItemTypeProvider**程式碼檔案中，預設的程式碼取代為下列程式碼，並儲存檔案。  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>建立 Visual Studio 專案範本
 藉由建立專案範本，您可以讓其他開發人員建立 SharePoint 專案包含站台資料行專案項目。 SharePoint 專案範本包含所需的所有專案在 Visual Studio 中，例如檔案 *.csproj*或 *.vbproj*並 *.vstemplate*檔案和檔案專屬於 SharePoint 專案。 如需詳細資訊，請參閱 <<c0> [ 建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 在此程序中，您可以建立空白的 SharePoint 專案來產生專屬於 SharePoint 專案的檔案。 您再將這些檔案加入 SiteColumnProjectTemplate 專案，讓它們包含在產生從這個專案的範本。 您也可以設定 SiteColumnProjectTemplate 專案檔，以指定的專案範本出現在**新的專案** 對話方塊。  
  
#### <a name="to-create-the-files-for-the-project-template"></a>若要建立專案範本檔案  
  
1.  開始的第二個執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有系統管理認證。  
  
2.  建立名為 SharePoint 2010 專案**BaseSharePointProject**。  
  
    > [!IMPORTANT]  
    >  在  **SharePoint 自訂精靈**，請勿選取**部署為伺服陣列方案**選項按鈕。  
  
3.  空白項目項目加入專案，並將然後命名的項目**Field1**。  
  
4.  儲存專案，並關閉第二個執行個體[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
5.  執行個體中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，已 SiteColumnProjectItem 方案開啟，在**方案總管**，開啟捷徑功能表**SiteColumnProjectTemplate**專案節點，選擇**新增**，然後選擇**現有的項目**。  
  
6.  在 [**加入現有項目**] 對話方塊中，開啟的檔案副檔名清單，然後選擇**的所有檔案 (\*。\*)**.  
  
7.  在包含 BaseSharePointProject 專案目錄中，選取 key.snk 檔案，然後再選擇**新增** 按鈕。  
  
    > [!NOTE]  
    >  在本逐步解說中，您所建立的專案範本會使用相同的 key.snk 檔案簽署使用範本建立的每個專案。 若要了解如何擴充這個範例，以建立不同的 key.snk 檔案以進行每個專案執行個體，請參閱[逐步解說： 使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
8.  重複步驟 5-8，從指定的子資料夾，BaseSharePointProject 目錄中加入下列檔案：  
  
    -   *\Field1\Elements.xml*  
  
    -   *\Field1\SharePointProjectItem.spdata*  
  
    -   *\Features\Feature1\Feature1.feature*  
  
    -   *\Features\Feature1\Feature1.Template.xml*  
  
    -   *\Package\Package.package*  
  
    -   *\Package\Package.Template.xml*  
  
     將這些檔案直接加入 SiteColumnProjectTemplate 專案;不要重建 Field1、 功能或封裝中的子資料夾的專案。 如需有關這些檔案的詳細資訊，請參閱 <<c0> [ 建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>若要設定開發人員如何探索新的專案 對話方塊中的專案範本
  
1.  在 **方案總管**，開啟捷徑功能表**SiteColumnProjectTemplate**專案節點，然後選擇**卸載專案**。 如果提示您變更儲存至任何檔案時，請選擇**是** 按鈕。  
  
2.  開啟捷徑功能表**SiteColumnProjectTemplate**節點，然後選擇**編輯 SiteColumnProjectTemplate.csproj**或**編輯 SiteColumnProjectTemplate.vbproj**.  
  
3.  在專案檔中，找出下列`VSTemplate`項目。  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  這個項目取代為下列 XML 程式碼。  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath`項目會指定當您建置專案時，專案範本建立所在的路徑中的其他資料夾。 此處指定的資料夾，確保專案範本會提供，客戶開啟時，才**新的專案**對話方塊方塊中，展開**SharePoint**節點，然後選擇  **2010年**節點。  
  
5.  儲存並關閉檔案。  
  
6.  在 [**方案總管] 中**，開啟捷徑功能表**SiteColumnProjectTemplate**專案，，然後選擇**重新載入專案**。  
  
## <a name="edit-the-project-template-files"></a>編輯專案範本檔案
 在 SiteColumnProjectTemplate 專案中，編輯下列檔案，以定義專案範本的行為：  
  
-   *AssemblyInfo.cs*或*AssemblyInfo.vb*  
  
-   *Elements.xml*  
  
-   *SharePointProjectItem.spdata*  
  
-   *Feature1.feature*  
  
-   *封裝*  
  
-   *SiteColumnProjectTemplate.vstemplate*  
  
-   *ProjectTemplate.csproj*或*ProjectTemplate.vbproj*  
  
 在下列程序中，您將這些檔案的一些新增可置換的參數。 可置換的參數是權杖的開始和結束都貨幣符號 （$） 字元。 當使用者使用這個專案範本建立專案時，Visual Studio 會自動使用的特定值取代這些參數在新的專案。 如需詳細資訊，請參閱 <<c0> [ 可置換的參數](../sharepoint/replaceable-parameters.md)。  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>若要編輯的 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案
  
1.  在 SiteColumnProjectTemplate 專案中，開啟*AssemblyInfo.cs*或是*AssemblyInfo.vb*檔案，並再加入頂端新增下列陳述式：  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     當**沙箱化方案**SharePoint 專案的屬性設定為 **，則為 True**，Visual Studio 會加入<xref:System.Security.AllowPartiallyTrustedCallersAttribute>AssemblyInfo 程式碼檔案。 不過，在專案範本的 AssemblyInfo 程式碼檔案不會匯入<xref:System.Security>預設的命名空間。 您必須將此新增**使用**或是**匯入**陳述式，以避免編譯錯誤。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-elementsxml-file"></a>若要編輯的 Elements.xml 檔案
  
1.  在 SiteColumnProjectTemplate 專案中的內容取代*Elements.xml*以下列 XML 檔案。  
  
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
  
     新的 XML 會新增`Field`定義站台資料行名稱、 其基底類型，並在其中列出站台資料行，在資源庫中的群組項目。 此檔案內容的相關資訊，請參閱[欄位定義結構描述](http://go.microsoft.com/fwlink/?LinkId=184290)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>若要編輯 SharePointProjectItem.spdata 檔案
  
1.  在 SiteColumnProjectTemplate 專案中的內容取代*SharePointProjectItem.spdata*以下列 XML 檔案。  
  
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
  
    -   變更`Type`的屬性`ProjectItem`項目相同的字串傳遞給<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>專案項目定義上 (`SiteColumnProjectItemTypeProvider`您稍早在本逐步解說中建立的類別)。  
  
    -   移除`SupportedTrustLevels`並`SupportedDeploymentScopes`屬性從`ProjectItem`項目。 這些屬性的值是不必要的因為在指定的信任層級和部署範圍`SiteColumnProjectItemTypeProvider`ProjectItemTypeDefinition 專案中的類別。  
  
     如需有關的內容 *.spdata*檔，請參閱[SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-feature1feature-file"></a>若要編輯 Feature1.feature 檔案
  
1.  在 SiteColumnProjectTemplate 專案中的內容取代*Feature1.feature*以下列 XML 檔案。  
  
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
  
    -   變更的值`Id`並`featureId`屬性`feature`項目`$guid4$`。  
  
    -   變更的值`itemId`的屬性`projectItemReference`項目`$guid2$`。  
  
     如需詳細資訊 *.feature*檔，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-packagepackage-file"></a>若要編輯封裝檔案
  
1.  在 SiteColumnProjectTemplate 專案中的內容取代*封裝*以下列 XML 檔案。  
  
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
  
    -   變更的值`Id`並`solutionId`屬性`package`項目`$guid3$`。  
  
    -   變更的值`itemId`的屬性`featureReference`項目`$guid4$`。  
  
     如需詳細資訊*套件*檔，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>若要編輯 sitecolumnprojecttemplate.vstemplate 檔案
  
1.  在 SiteColumnProjectTemplate 專案中，請以 XML 的下列各節的其中一個取代 SiteColumnProjectTemplate.vstemplate 檔案的內容。  
  
    -   如果您正在建立 Visual C# 專案範本，請使用下列 XML 程式碼。  
  
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
  
    -   如果您要建立 Visual Basic 專案範本，請使用下列 XML 程式碼。  
  
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
  
    -   設定組`Name`值的項目**站台的資料行**。 (此名稱會出現在**新的專案**對話方塊)。  
  
    -   新增`ProjectItem`filethat 每個元素的包含在每個專案執行個體。  
  
    -   使用命名空間"http://schemas.microsoft.com/developer/vstemplate/2005」。 其他專案檔案，在此解決方案使用 「http://schemas.microsoft.com/developer/msbuild/2003"命名空間。 因此，會產生 XML 結構描述的警告訊息，但您可以忽略這些在本逐步解說。  
  
     如需有關的內容 *.vstemplate*檔，請參閱[Visual Studio 範本結構描述參考](/visualstudio/extensibility/visual-studio-template-schema-reference)。  
  
2.  儲存並關閉檔案。  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>若要編輯的 projecttemplate.csproj 或 projecttemplate.vbproj 檔案
  
1.  在 SiteColumnProjectTemplate 專案中的內容取代*ProjectTemplate.csproj*檔案或*ProjectTemplate.vbproj* XML 的下列各節的其中一個檔案。  
  
    -   如果您正在建立 Visual C# 專案範本，請使用下列 XML 程式碼。  
  
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
  
    1.  如果您要建立 Visual Basic 專案範本，請使用下列 XML 程式碼。  
  
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
  
    -   使用`TargetFrameworkVersion`項目來指定.NET Framework 3.5，而不是 4.5。  
  
    -   新增`SignAssembly`和`AssemblyOriginatorKeyFile`来簽署專案輸出項目。  
  
    -   新增`Reference`組件的項目參考 SharePoint 專案使用。  
  
    -   會將元素加入每個預設檔案在專案中，這類*Elements.xml*並*SharePointProjectItem.spdata*。  
  
2.  儲存並關閉檔案。  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>建立 VSIX 封裝來部署專案範本
 若要部署的擴充功能，使用 VSIX 專案中的**SiteColumnProjectItem**方案以建立 VSIX 封裝。 首先，設定 VSIX 套件藉由修改 source.extension.vsixmanifest 檔案中包含在 VSIX 專案。 建立方案，然後建立 VSIX 封裝。  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>若要設定及建立 VSIX 封裝  
  
1.  在 **方案總管**，請在**SiteColumnProjectItem**專案中，開啟 source.extension.vsixmanifest 檔案中的資訊清單編輯器。  
  
     Source.extension.vsixmanifest 檔案中會是所有的 VSIX 套件需要 extension.vsixmanifest 檔案的基礎。 如需有關這個檔案的詳細資訊，請參閱 < [VSIX 延伸結構描述 1.0 參考](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。  
  
2.  在  **Product Name**方塊中，輸入**站台的資料行**。  
  
3.  在 **作者**方塊中，輸入**Contoso**。  
  
4.  在 **描述**方塊中，輸入**建立站台的資料行的 SharePoint 專案**。  
  
5.  選擇**資產**索引標籤，然後選擇**新增** 按鈕。  
  
     **加入新資產**對話方塊隨即開啟。  
  
6.  在 **型別**清單中，選擇**Microsoft.VisualStudio.ProjectTemplate**。  
  
    > [!NOTE]  
    >  這個值會對應到`ProjectTemplate`extension.vsixmanifest 檔案中的項目。 此項目可識別包含專案範本的 VSIX 套件中的子資料夾。 如需詳細資訊，請參閱 < [ProjectTemplate 項目 （VSX 結構描述）](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1)。  
  
7.  在 **來源**清單中，選擇**目前方案中的專案**。  
  
8.  在 [**專案**清單，然後選擇**SiteColumnProjectTemplate**，然後選擇 **[確定]** ] 按鈕。  
  
9. 選擇**新增**按鈕一次。  
  
     **加入新資產**對話方塊隨即開啟。  
  
10. 在 **型別**清單中，選擇**Microsoft.VisualStudio.MefComponent**。  
  
    > [!NOTE]  
    >  這個值會對應到`MefComponent`extension.vsixmanifest 檔案中的項目。 這個元素會指定在 VSIX 封裝中的延伸模組組件名稱。 如需詳細資訊，請參閱 < [MEFComponent 項目 （VSX 結構描述）](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551)。  
  
11. 在 **來源**清單中，選擇**目前方案中的專案**。  
  
12. 在 [**專案**清單中，選擇**ProjectItemTypeDefinition**，然後選擇 **[確定]** ] 按鈕。  
  
13. 在功能表列上選擇 **建置** > **建置方案**，然後確認專案編譯無誤。  
  
## <a name="test-the-project-template"></a>測試專案範本
 您現在已準備好測試專案範本。 首先，啟動偵錯 SiteColumnProjectItem 方案在 Visual Studio 的實驗執行個體。 然後，測試**站台的資料行**Visual Studio 的實驗執行個體中的專案。 最後，建置並執行 SharePoint 專案，以確認站台的資料行可以正常運作。  
  
#### <a name="to-start-debugging-the-solution"></a>若要啟動偵錯方案  
  
1.  使用系統管理認證，重新啟動 Visual Studio，然後開啟 SiteColumnProjectItem 解決方案。  
  
2.  
  
3.  在 SiteColumnProjectItemTypeProvider 程式碼檔案中，將中斷點新增至程式碼中的第一行`InitializeType`方法，然後選擇**F5**鍵開始偵錯。  
  
     Visual Studio 會 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 安裝擴充功能，並啟動 Visual Studio 的實驗執行個體。 在 Visual Studio 這個執行個體中，您將測試專案項目。  
  
#### <a name="to-test-the-project-in-visual-studio"></a>若要在 Visual Studio 中測試專案  
  
1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**檔案** > **新增** > **專案**。  
  
2.  依序展開**Visual C#** 或**Visual Basic**節點 （取決於您的專案範本支援語言），展開**SharePoint** ] 節點，然後選擇 [ **2010年**節點。  
  
3.  在專案範本清單中，選擇**站台的資料行**範本。  
  
4.  在 [**名稱**方塊中，輸入**SiteColumnTest** ，然後選擇**確定**] 按鈕。  
  
     在 **方案總管**，新的專案會顯示與專案項目，稱為**Field1**。  
  
5.  確認停止您稍早在設定的中斷點上的 Visual Studio 的其他執行個體中的程式碼`InitializeType`方法，然後選擇**F5**鍵繼續偵錯專案。  
  
6.  在**方案總管 中**，選擇**Field1**節點，然後選擇**F4**索引鍵。  
  
     **屬性**視窗隨即開啟。  
  
7.  在 [屬性] 清單中，確認屬性**屬性範例**隨即出現。  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>若要在 SharePoint 中測試網站資料行  
  
1.  在 **方案總管**，選擇**SiteColumnTest**節點。  
  
2.  在 **屬性**視窗中，旁邊的文字方塊中**站台 URL**屬性，輸入**http://localhost**。  
  
     此步驟中指定您想要用於偵錯在開發電腦上的本機 SharePoint 網站。  
  
    > [!NOTE]  
    >  **站台 URL**屬性是空的預設值，因為網站欄專案範本未提供精靈來建立專案時，收集此值。 若要了解如何新增精靈，這個值會要求開發人員，並接著在新的專案中設定這個屬性，請參閱[逐步解說： 使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
3.  選擇 **F5** 鍵。  
  
     網站資料行是封裝並部署到 SharePoint 網站中指定**站台 URL**專案屬性。 Web 瀏覽器中開啟此站台的預設頁面。  
  
    > [!NOTE]  
    >  如果**指令碼偵錯已停用** 對話方塊出現時，選擇**是**按鈕以繼續進行偵錯專案。  
  
4.  在上**站台動作**功能表上，選擇**站台設定**。  
  
5.  在 **站台設定**頁面的 **組件庫**清單中，選擇**站台的資料行**連結。  
  
6.  在 網站資料行的清單中，確認**自訂資料行**群組中包含名為的資料行**SiteColumnTest**。  
  
7.  關閉網頁瀏覽器。  
  
## <a name="clean-up-the-development-computer"></a>清除開發電腦
 完成測試專案之後，請從 Visual Studio 的實驗執行個體中移除專案範本。  
  
#### <a name="to-clean-up-the-development-computer"></a>清除開發電腦  
  
1.  在實驗性 Visual Studio 執行個體，在功能表列上，選擇**工具** > **擴充功能和更新**。  
  
     [擴充功能和更新] 對話方塊隨即開啟。  
  
2.  在延伸模組清單中，選擇**網站資料行**延伸模組，然後選擇**解除安裝** 按鈕。  
  
3.  在出現的對話方塊中，選擇**是**按鈕，以確認您想要解除安裝擴充功能。  
  
4.  選擇**關閉**按鈕以完成解除安裝。  
  
5.  關閉 Visual Studio （實驗性執行個體和 SiteColumnProjectItem 方案已開啟的 Visual Studio 執行個體） 的兩個執行個體。  
  
## <a name="next-steps"></a>後續步驟
 完成本逐步解說之後，您可以新增專案範本的精靈。 當使用者建立的網站欄專案時，精靈會要求使用者輸入網站 URL，要用於偵錯，以及新的解決方案是沙箱化，以及精靈設定新的專案使用這項資訊。 精靈也會收集資訊 （例如基底型別和要在其中列出站台的資料行組件庫中的資料行群組） 的資料行，並將這項資訊來*Elements.xml*新專案中的檔案。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 使用專案範本，第 2 部分建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## <a name="see-also"></a>另請參閱
 [逐步解說： 使用專案範本，第 2 部分中建立網站資料行專案項目](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [定義自訂 SharePoint 專案項目類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [將資料儲存在 SharePoint 專案系統的擴充功能](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [將自訂的資料產生關聯的 SharePoint 工具擴充功能](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
