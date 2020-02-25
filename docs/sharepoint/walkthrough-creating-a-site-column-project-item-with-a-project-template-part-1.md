---
title: 使用專案範本建立網站資料行專案專案（第1部分）
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 843d56482a82c2a8210de50455753c9703698503
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557839"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>逐步解說：使用專案範本建立網站資料行專案專案（第1部分）
  SharePoint 專案是一個或多個 SharePoint 專案專案的容器。 您可以藉由建立您自己的 SharePoint 專案專案類型，然後將它們與專案範本產生關聯，在 Visual Studio 中擴充 SharePoint 專案系統。 在此逐步解說中，您將定義用來建立網站資料行的專案專案類型，然後您會建立專案範本，以用來建立包含網站資料行專案專案的新專案。

 本逐步解說將示範下列工作：

- 建立 Visual Studio 延伸模組，為網站資料行定義新類型的 SharePoint 專案專案。 專案專案類型包含一個簡單的自訂屬性，它會出現在 [**屬性**] 視窗中。

- 建立專案專案的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 專案範本。

- 建立 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能（VSIX）封裝，以部署專案範本和擴充元件。

- 正在對專案專案進行調試和測試。

  這是一種獨立的逐步解說。 完成本逐步解說之後，您可以藉由將 wizard 新增至專案範本，來增強專案專案。 如需詳細資訊，請參閱[逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。

> [!NOTE]
> 如需一系列範例工作流程，請參閱[SharePoint 工作流程範例](/sharepoint/dev/general-development/sharepoint-workflow-samples)。

## <a name="prerequisites"></a>Prerequisites
 您需要在開發電腦上有下列元件，才能完成此逐步解說：

- 支援的 Microsoft Windows、SharePoint 和 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]版本。

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]。 本逐步解說會使用 SDK 中的**Vsix 專案**範本來建立 vsix 封裝，以部署專案專案。 如需詳細資訊，請參閱[Visual Studio 中的擴充 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)。

  下列概念的知識很有説明，但並非必要，無法完成逐步解說：

- SharePoint 中的網站資料行。 如需詳細資訊，請參閱資料[行](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))。

- Visual Studio 中的專案範本。 如需詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。

## <a name="create-the-projects"></a>建立專案
 若要完成此逐步解說，您需要建立三個專案：

- VSIX 專案。 此專案會建立 VSIX 封裝，以部署網站資料行專案專案和專案範本。

- 專案範本專案。 這個專案會建立一個專案範本，可用來建立新的 SharePoint 專案，其中包含網站資料行專案專案。

- 類別庫專案。 這個專案會實作為定義網站資料行專案專案行為的 Visual Studio 延伸模組。

  藉由建立專案來啟動逐步解說。

#### <a name="to-create-the-vsix-project"></a>建立 VSIX 專案

1. 啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

3. 在 [**新增專案**] 對話方塊的頂端，確定已在 .NET Framework 版本清單中選擇 [ **.NET Framework 4.5** ]。

4. 展開 [ **Visual Basic** ] 或 [**視覺效果C#**  ] 節點，然後選擇 [擴充性 **] 節點。**

    > [!NOTE]
    > 只有在您安裝 Visual Studio SDK 時，才能使用擴充**性節點。** 如需詳細資訊，請參閱本主題稍早的必要條件一節。

5. 在專案範本清單中，選擇 [ **VSIX 專案**]。

6. 在 [**名稱**] 方塊中，輸入**SiteColumnProjectItem**，然後選擇 [**確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將**SiteColumnProjectItem**專案新增至**方案總管**。

#### <a name="to-create-the-project-template-project"></a>若要建立專案範本專案

1. 在**方案總管**中，開啟 [方案] 節點的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增專案**]。

2. 在 [**新增專案**] 對話方塊的頂端，確定已在 .NET Framework 版本清單中選擇 [ **.NET Framework 4.5** ]。

3. 展開 [**視覺C#效果**] 或 [ **Visual Basic** ] 節點，然後選擇 [擴充性 **] 節點。**

4. 在專案範本清單中，選擇 [  **C#專案範本**] 或 [ **Visual Basic 專案範本**] 範本。

5. 在 [**名稱**] 方塊中，輸入**SiteColumnProjectTemplate**，然後選擇 [**確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將**SiteColumnProjectTemplate**專案新增至方案。

6. 從專案中刪除 Class1 程式碼檔案。

7. 如果您建立了 Visual Basic 專案，請同時從專案中刪除下列檔案：

    - *MyApplication. 設計工具 .vb*

    - MyApplication myapp

    - *Resources. Designer .vb*

    - *Resources .resx*

    - *設定. 設計工具 .vb*

    - 設定

#### <a name="to-create-the-extension-project"></a>若要建立擴充功能專案

1. 在**方案總管**中，開啟 [方案] 節點的快捷方式功能表，選擇 [**加入**]，然後選擇 [**新增專案**]。

2. 在 [**新增專案**] 對話方塊的頂端，確定已在 .NET Framework 版本清單中選擇 [ **.NET Framework 4.5** ]。

3. 展開 [**視覺C#效果**] 或 [ **Visual Basic** ] 節點，選擇 [ **Windows** ] 節點，然後選擇 [**類別庫**] 範本。

4. 在 [**名稱**] 方塊中，輸入**ProjectItemTypeDefinition** ，然後選擇 [**確定]** 按鈕。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將**ProjectItemTypeDefinition**專案新增至方案，並開啟預設的 Class1 程式碼檔案。

5. 從專案中刪除 Class1 程式碼檔案。

## <a name="configure-the-extension-project"></a>設定擴充功能專案
 加入程式碼檔案和元件參考，以設定擴充功能專案。

#### <a name="to-configure-the-project"></a>若要設定專案

1. 在 ProjectItemTypeDefinition 專案中，加入名為**SiteColumnProjectItemTypeProvider**的程式碼檔案。

2. 在功能表列上，選擇 [專案] >  [加入參考]。

3. 在 [**參考管理員-ProjectItemTypeDefinition** ] 對話方塊中，展開 [**元件**] 節點，選擇 [**架構**] 節點，然後選取 [system.workflow.componentmodel.activity] 核取方塊。

4. 選擇 [**擴充**功能] 節點，選取 [VisualStudio] 元件旁的核取方塊，然後選擇 [**確定]** 按鈕。

## <a name="define-the-new-sharepoint-project-item-type"></a>定義新的 SharePoint 專案專案類型
 建立可執行 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 介面的類別，以定義新專案專案類型的行為。 每當您想要定義新類型的專案專案時，就會執行此介面。

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>若要定義新的 SharePoint 專案專案類型

1. 在**SiteColumnProjectItemTypeProvider**程式碼檔案中，將預設程式碼取代為下列程式碼，然後儲存檔案。

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>建立 Visual Studio 專案範本
 藉由建立專案範本，您可以讓其他開發人員建立包含網站資料行專案專案的 SharePoint 專案。 SharePoint 專案範本包含 Visual Studio 中所有專案所需的檔案，例如 *.csproj*或*vbproj*和 *.vstemplate*檔案，以及 SharePoint 專案特有的檔案。 如需詳細資訊，請參閱[建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 在這個程式中，您會建立空白的 SharePoint 專案，以產生 SharePoint 專案特有的檔案。 接著，您會將這些檔案新增至 SiteColumnProjectTemplate 專案，使其包含在此專案所產生的範本中。 您也可以設定 SiteColumnProjectTemplate 專案檔案，以指定專案範本出現在 [**新增專案**] 對話方塊中的位置。

#### <a name="to-create-the-files-for-the-project-template"></a>若要建立專案範本的檔案

1. 使用系統管理認證啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的第二個實例。

2. 建立名為**BaseSharePointProject**的 SharePoint 2010 專案。

   > [!IMPORTANT]
   > 在**SharePoint 自訂嚮導**中，不要選取 [**部署為伺服器陣列方案**] 選項按鈕。

3. 將空白元素專案新增至專案，然後將專案命名為**Field1**。

4. 儲存專案，然後關閉 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的第二個實例。

5. 在開啟 SiteColumnProjectItem 方案的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 實例中，于**方案總管**中開啟**SiteColumnProjectTemplate**專案節點的快捷方式功能表，選擇 [**新增**]，然後選擇 [**現有專案**]。

6. 在 [**加入現有專案**] 對話方塊中，開啟副檔名清單，然後選擇 [所有檔案] **（\*.\*）** 。

7. 在包含 BaseSharePointProject 專案的目錄中，選取 [金鑰 .snk 檔案]，然後選擇 [**新增**] 按鈕。

   > [!NOTE]
   > 在此逐步解說中，您所建立的專案範本會使用相同的金鑰 .snk 檔案來簽署使用範本所建立的每個專案。 若要瞭解如何擴充此範例，為每個專案實例建立不同的金鑰 .snk 檔案，請參閱[逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。

8. 重複步驟5-8，從 BaseSharePointProject 目錄中指定的子資料夾新增下列檔案：

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     將這些檔案直接新增至 SiteColumnProjectTemplate 專案;請勿在專案中重新建立 Field1、Features 或 Package 子資料夾。 如需這些檔案的詳細資訊，請參閱[建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>設定開發人員在 [新增專案] 對話方塊中探索專案範本的方式

1. 在**方案總管**中，開啟**SiteColumnProjectTemplate**專案節點的快捷方式功能表，然後選擇 **[卸載專案**]。 如果系統提示您儲存任何檔案的變更，請選擇 [**是]** 按鈕。

2. 再次開啟 [ **SiteColumnProjectTemplate** ] 節點的快捷方式功能表，然後選擇 [**編輯 SiteColumnProjectTemplate** ] 或 [**編輯 SiteColumnProjectTemplate vbproj**]。

3. 在專案檔中，找出下列 `VSTemplate` 元素。

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. 以下列 XML 取代此元素。

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     當您建立專案時，`OutputSubPath` 專案會在路徑下指定其他資料夾，以在其中建立專案範本。 此處指定的資料夾會確保只有當客戶開啟 [**新增專案**] 對話方塊、展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點時，才能使用此專案範本。

5. 儲存並關閉檔案。

6. 在**方案總管**中，開啟**SiteColumnProjectTemplate**專案的快捷方式功能表，然後選擇 [**重載專案**]。

## <a name="edit-the-project-template-files"></a>編輯專案範本檔案
 在 SiteColumnProjectTemplate 專案中，編輯下列檔案以定義專案範本的行為：

- *AssemblyInfo.cs*或*AssemblyInfo .vb*

- *元素 .xml*

- *SharePointProjectItem. .spdata*

- *Feature1. 功能*

- *Package. package*

- *SiteColumnProjectTemplate .vstemplate*

- *ProjectTemplate .csproj*或*ProjectTemplate. vbproj*

  在下列程式中，您會將可取代的參數新增至其中一些檔案。 可取代的參數是以貨幣符號（$）字元開頭和結尾的 token。 當使用者使用此專案範本來建立專案時，Visual Studio 會自動以特定值取代新專案中的這些參數。 如需詳細資訊，請參閱可[取代的參數](../sharepoint/replaceable-parameters.md)。

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>編輯 AssemblyInfo.cs 或 AssemblyInfo .vb 檔案

1. 在 SiteColumnProjectTemplate 專案中，開啟*AssemblyInfo.cs*或*AssemblyInfo*檔案，然後將下列語句新增至其頂端：

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     當 SharePoint 專案的**沙箱化方案**屬性設定為**True**時，Visual Studio 會將 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 新增至 AssemblyInfo 程式碼檔案。 不過，專案範本中的 AssemblyInfo 程式碼檔案預設不會匯入 <xref:System.Security> 命名空間。 您必須**使用**或**Imports**語句來加入此，以避免編譯錯誤。

2. 儲存並關閉檔案。

#### <a name="to-edit-the-elementsxml-file"></a>編輯元素 .xml 檔案

1. 在 SiteColumnProjectTemplate 專案中，將*元素 .xml*檔案的內容取代為下列 xml。

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

     新的 XML 會加入一個 `Field` 專案，定義網站資料行的名稱、其基底類型，以及要在其中列出資源庫中網站資料行的群組。 如需這個檔案內容的詳細資訊，請參閱[欄位定義架構](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14))。

2. 儲存並關閉檔案。

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>編輯 SharePointProjectItem .spdata 檔案

1. 在 SiteColumnProjectTemplate 專案中，將*SharePointProjectItem. .spdata*檔案的內容取代為下列 XML。

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

   - 將 `ProjectItem` 元素的 `Type` 屬性，變更為傳遞至專案專案定義（您稍早在本逐步解說中建立的 `SiteColumnProjectItemTypeProvider` 類別）之 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 的相同字串。

   - 從 `ProjectItem` 元素移除 `SupportedTrustLevels` 和 `SupportedDeploymentScopes` 屬性。 這些屬性值是不必要的，因為信任層級和部署範圍是在 ProjectItemTypeDefinition 專案的 `SiteColumnProjectItemTypeProvider` 類別中指定。

     如需有關 *.spdata*檔內容的詳細資訊，請參閱[SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)。

2. 儲存並關閉檔案。

#### <a name="to-edit-the-feature1feature-file"></a>編輯 Feature1 功能檔案

1. 在 SiteColumnProjectTemplate 專案中，將*Feature1. 功能*檔案的內容取代為下列 XML。

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

   - 將 `feature` 元素的 `Id` 和 `featureId` 屬性值變更為 `$guid4$`。

   - 將 `projectItemReference` 元素的 `itemId` 屬性值變更為 `$guid2$`。

     如需有關*功能*檔案的詳細資訊，請參閱[建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

2. 儲存並關閉檔案。

#### <a name="to-edit-the-packagepackage-file"></a>編輯封裝檔案。封裝檔案

1. 在 SiteColumnProjectTemplate 專案中，將*package*檔案的內容取代為下列 XML。

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

   - 將 `package` 元素的 `Id` 和 `solutionId` 屬性值變更為 `$guid3$`。

   - 將 `featureReference` 元素的 `itemId` 屬性值變更為 `$guid4$`。

     如需有關*封裝*檔案的詳細資訊，請參閱[建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

2. 儲存並關閉檔案。

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>若要編輯 sitecolumnprojecttemplate .vstemplate 檔案

1. 在 SiteColumnProjectTemplate 專案中，將 SiteColumnProjectTemplate 的內容取代為下列其中一個 XML 區段。

   - 如果您要建立視覺C#專案範本，請使用下列 XML。

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

   - 如果您要建立 Visual Basic 專案範本，請使用下列 XML。

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

   - 將 `Name` 專案設定為 [值**網站**] 資料行。 （這個名稱會出現在 [**新增專案**] 對話方塊中）。

   - 針對每個專案實例中包含的每個 filethat 加入 `ProjectItem` 元素。

   - 使用命名空間 `http://schemas.microsoft.com/developer/vstemplate/2005`。 此方案中的其他專案檔會使用 `http://schemas.microsoft.com/developer/msbuild/2003` 命名空間。 因此，將會產生 XML 架構警告訊息，但在本逐步解說中，您可以忽略它們。

     如需 *.vstemplate*檔案內容的詳細資訊，請參閱[Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)。

2. 儲存並關閉檔案。

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>若要編輯 projecttemplate .csproj 或 projecttemplate. vbproj 檔案

1. 在 SiteColumnProjectTemplate 專案中，將*ProjectTemplate*檔案或*ProjectTemplate*的內容取代為下列其中一個 XML 區段。

    - 如果您要建立視覺C#專案範本，請使用下列 XML。

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

    1. 如果您要建立 Visual Basic 專案範本，請使用下列 XML。

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

    - 使用 `TargetFrameworkVersion` 元素來指定 .NET Framework 3.5，而不是4.5。

    - 加入 `SignAssembly` 和 `AssemblyOriginatorKeyFile` 元素，以簽署專案輸出。

    - 加入 SharePoint 專案所使用之元件參考的 `Reference` 元素。

    - 為專案中的每個預設檔案加入元素，例如*元素 .xml*和*SharePointProjectItem. .spdata*。

2. 儲存並關閉檔案。

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>建立 VSIX 封裝以部署專案範本
 若要部署擴充功能，請使用**SiteColumnProjectItem**方案中的 vsix 專案來建立 vsix 封裝。 首先，藉由修改包含在 VSIX 專案中的 extension.vsixmanifest 檔案來設定 VSIX 封裝。 然後，藉由建立方案來建立 VSIX 封裝。

#### <a name="to-configure-and-create-the-vsix-package"></a>設定和建立 VSIX 封裝

1. 在**方案總管**的 [ **SiteColumnProjectItem** ] 專案中，在 [資訊清單編輯器] 中開啟 extension.vsixmanifest 檔案。

     Extension.vsixmanifest 檔案是所有 VSIX 封裝所需之 extension.vsixmanifest 檔案的基礎。 如需這個檔案的詳細資訊，請參閱[VSIX 延伸模組架構1.0 參考](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)。

2. 在 [**產品名稱**] 方塊中，輸入**Site Column**。

3. 在 [**作者**] 方塊中，輸入**Contoso**。

4. 在 [**描述**] 方塊中，輸入**用來建立網站資料行的 SharePoint 專案**。

5. 選擇 [**資產**] 索引標籤，然後選擇 [**新增**] 按鈕。

     [**加入新資產**] 對話方塊隨即開啟。

6. 在 [**類型**] 清單中，選擇 [ **VisualStudio ProjectTemplate**]。

    > [!NOTE]
    > 這個值會對應至 extension.vsixmanifest 檔案中的 `ProjectTemplate` 元素。 這個元素會識別包含專案範本之 VSIX 封裝中的子資料夾。 如需詳細資訊，請參閱[ProjectTemplate 元素（VSX 架構）](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\))。

7. 在 [**來源**] 清單中，選擇 [**目前方案] 中的專案**。

8. 在 [**專案**] 清單中，選擇 [ **SiteColumnProjectTemplate**]，然後選擇 [**確定]** 按鈕。

9. 再次選擇 [**新增**] 按鈕。

     [**加入新資產**] 對話方塊隨即開啟。

10. 在 [**類型**] 清單中，選擇 [ **VisualStudio [microsoft.visualstudio.mefcomponent]** ]。

    > [!NOTE]
    > 這個值會對應至 extension.vsixmanifest 檔案中的 `MefComponent` 元素。 這個元素會指定 VSIX 封裝中的擴充元件名稱。 如需詳細資訊，請參閱[[Microsoft.visualstudio.mefcomponent] 元素（VSX 架構）](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))。

11. 在 [**來源**] 清單中，選擇 [**目前方案] 中的專案**。

12. 在 [**專案**] 清單中，選擇 [ **ProjectItemTypeDefinition**]，然後選擇 [**確定]** 按鈕。

13. 在功能表列上，選擇 [**組建**] [ > ] [**組建方案**]，然後確認專案編譯無誤。

## <a name="test-the-project-template"></a>測試專案範本
 您現在已準備好測試專案範本。 首先，在 Visual Studio 的實驗實例中，開始對 SiteColumnProjectItem 方案進行調試。 然後，在 Visual Studio 的實驗實例中測試**網站資料行**專案。 最後，建立並執行 SharePoint 專案，以確認 [網站] 欄是否如預期般運作。

#### <a name="to-start-debugging-the-solution"></a>開始對方案進行調試

1. 使用系統管理認證重新開機 Visual Studio，然後開啟 SiteColumnProjectItem 解決方案。

2. 在 SiteColumnProjectItemTypeProvider 程式碼檔案中，將中斷點新增至 `InitializeType` 方法中的第一行程式碼，然後選擇**F5**鍵開始進行偵錯工具。

     Visual Studio 會將擴充功能安裝至%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0，並啟動 Visual Studio 的實驗實例。 您將在 Visual Studio 的這個實例中測試專案專案。

#### <a name="to-test-the-project-in-visual-studio"></a>若要在 Visual Studio 中測試專案

1. 在 Visual Studio 的實驗實例中，于功能表列**上選擇 [** 檔案] [檔案] [ > **新增** > **專案**]。

2. 展開 [**視覺C#效果**] 或 [ **Visual Basic** ] 節點（視您的專案範本支援的語言而定），展開 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在專案範本清單中，選擇 [網站] 資料**行**範本。

4. 在 [**名稱**] 方塊中，輸入**SiteColumnTest** ，然後選擇 [**確定]** 按鈕。

     在**方案總管**中，會出現新的專案，其中包含名為**Field1**的專案專案。

5. 確認 Visual Studio 另一個實例中的程式碼會在您稍早于 `InitializeType` 方法中設定的中斷點上停止，然後選擇**F5**鍵繼續進行專案的偵錯工具。

6. 在**方案總管**中，選擇 [ **Field1** ] 節點，然後選擇**F4**鍵。

     [屬性] 視窗隨即開啟。

7. 在 [屬性] 清單中，確認已顯示 [屬性**範例] 屬性**。

#### <a name="to-test-the-site-column-in-sharepoint"></a>測試 SharePoint 中的網站資料行

1. 在**方案總管**中，選擇 [ **SiteColumnTest** ] 節點。

2. 在 [**屬性**] 視窗中，于 [**網站 URL** ] 屬性旁邊的文字方塊中，輸入 **http://localhost** 。

     此步驟會指定開發電腦上您想要用來進行偵錯工具的本機 SharePoint 網站。

    > [!NOTE]
    > 根據預設，[網站**URL** ] 屬性是空的，因為 [網站資料行] 專案範本未提供在建立專案時收集此值的 wizard。 若要瞭解如何加入會詢問開發人員此值的嚮導，然後在新的專案中設定這個屬性，請參閱[逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。

3. 選擇 **F5** 鍵。

     [網站] 資料行會封裝並部署到專案的 [**網站 URL** ] 屬性中所指定的 SharePoint 網站。 網頁瀏覽器會開啟至此網站的預設頁面。

    > [!NOTE]
    > 如果出現 [**腳本調試已停用**] 對話方塊，請選擇 [**是]** 按鈕以繼續進行專案的 debug。

4. 在 [**網站動作**] 功能表上，選擇 [**網站設定**]。

5. 在 [**網站設定**] 頁面的 [資源**庫**] 清單下，選擇 [**網站資料行**] 連結。

6. 在 [網站資料行] 清單中，確認 [**自訂資料行**] 群組包含名為**SiteColumnTest**的資料行。

7. 關閉網頁瀏覽器。

## <a name="clean-up-the-development-computer"></a>清理開發電腦
 完成專案測試之後，請從 Visual Studio 的實驗實例中移除專案範本。

#### <a name="to-clean-up-the-development-computer"></a>清理開發電腦

1. 在 Visual Studio 的實驗實例中，選擇功能表列上的 [**工具**] > [**擴充功能和更新**]。

     [擴充功能和更新] 對話方塊隨即開啟。

2. 在擴充功能清單中，選擇 [**網站**] 資料行延伸模組，然後選擇 [**卸載**] 按鈕。

3. 在出現的對話方塊中，選擇 [**是**] 按鈕以確認您要卸載擴充功能。

4. 選擇 [**關閉**] 按鈕以完成卸載。

5. 關閉 Visual Studio 的兩個實例（實驗實例和 SiteColumnProjectItem 方案開啟所在的 Visual Studio 實例）。

## <a name="next-steps"></a>後續步驟
 完成本逐步解說之後，您可以將 wizard 加入專案範本。 當使用者建立網站資料行專案時，此 wizard 會要求使用者提供用於進行偵測的網站 URL，以及是否要將新的方案設定為沙箱，而 wizard 會使用此資訊來設定新的專案。 此 wizard 也會收集資料行的相關資訊（例如，要在 [網站] 資料行庫中列出資料行的基底類型和群組），並將這項資訊新增至新專案中的*Elements .xml*檔案。 如需詳細資訊，請參閱[逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：使用專案範本建立網站資料行專案專案（第2部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [定義自訂 SharePoint 專案專案類型](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [為 SharePoint 專案專案建立專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [儲存 SharePoint 專案系統延伸模組中的資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [將自訂資料與 SharePoint 工具擴充功能產生關聯](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)