---
title: " (Visual Studio 範本的 .Vstemplate 元素) |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8219f12eed091858a43c2bd5092b8b06f8320bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422893"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

包含專案範本、專案範本或入門套件的所有中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Type`|將範本識別為專案範本或專案範本。 這個屬性的值可以是 `Project` 或 `Item` 。|  
|`Version`|指定範本的版本號碼。 和中 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 的範本具有 `Version` 的屬性值 `3.0.0` 。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定將範本分類的資料，並定義該範本在 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中顯示的方式。|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定範本的內容。|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|選擇性項目。|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|選擇性項目。|  
  
### <a name="parent-elements"></a>父項目  
 無。  
  
## <a name="remarks"></a>備註  
 `VSTemplate`元素是 .vstemplate 檔案的根項目。  
  
## <a name="example"></a>範例  
 下列範例會顯示應用程式專案範本的中繼資料 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
