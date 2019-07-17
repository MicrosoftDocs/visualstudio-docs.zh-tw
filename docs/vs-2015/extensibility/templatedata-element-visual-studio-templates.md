---
title: TemplateData 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 209d8066d232c63364a045aee6b8dd2153033666
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186445"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。  
  
 \<VSTemplate >  
 \<TemplateData >  
  
## <a name="syntax"></a>語法  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[名稱](../extensibility/name-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定範本的名稱，因為它會出現在其中一個**新的專案**或**加入新項目**對話方塊。|  
|[描述](../extensibility/description-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定範本的描述中所顯示的樣子**新的專案**或**加入新項目** 對話方塊。|  
|[圖示](../extensibility/icon-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定的路徑和檔名做為圖示時，就會出現在其中一個映像檔的**新的專案**或**加入新項目**對話方塊中，範本。|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|必要項目。<br /><br /> 將分類的專案範本，使其出現在中指定的群組**新的專案** 對話方塊。|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 將分類專案範本，使它出現在中指定的子類別目錄之下**新的專案** 對話方塊。|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定範本 id。|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定範本的群組識別碼。|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定值，因為它會出現在其中一個用來排列的範本，在相同類別中，其他範本之間**新的專案**或是**加入新項目** 對話方塊。|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定是否要包含的資料夾建立在具現化的專案。|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 建立時，請指定 Visual Studio 專案系統會產生的專案或項目的名稱。|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定 Visual Studio 專案系統是否會在建立時產生的預設名稱的專案或項目。|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定專案是否可以建立為暫存專案。|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定是否**瀏覽** 按鈕位於**新的專案**對話方塊，讓使用者可以輕鬆地修改儲存新專案的預設目錄。|  
|[隱藏](../extensibility/hidden-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定是否在該範本會出現**新的專案**或**加入新項目** 對話方塊。|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定的數目會顯示在範本的父類別**新的專案** 對話方塊。|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|選擇性項目。|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定是否**位置**中的文字方塊**新的專案** 對話方塊中已啟用、 停用，或隱藏專案範本。|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 如果範本只支援特定的最小版本和更新的版本，如果有的話，.NET framework，請使用此項目。|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定樣板是否支援 web 專案的主版頁面。|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定樣板是否支援程式碼分離或程式碼後置頁面模型中，web 專案。|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定是否範本是相同的多種語言，以及是否**語言**選項可從**新的專案** 對話方塊。|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定專案範本的目標平台。 這個項目可讓您指定的專案範本用來建立[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]應用程式。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要項目。<br /><br /> 包含專案範本、 項目範本，或入門套件的所有中繼資料。|  
  
## <a name="remarks"></a>備註  
 `TemplateData` 是必要項目。  
  
 如果您未包含選擇性的項目，則會使用該元素的預設值。  
  
## <a name="example"></a>範例  
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]應用程式。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
