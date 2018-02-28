---
title: "VSTemplate 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1c9fe87ae48c705e447b4fc5bd2834a417c4e8d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 項目 (Visual Studio 範本)
包含有關專案範本、 項目範本或入門套件的所有中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Type`|識別做為專案範本或項目範本的範本。 這個屬性可以具有值為`Project`或`Item`。|  
|`Version`|指定範本的版本號碼。 中的範本[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]和[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]有`Version`屬性值為`3.0.0`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定資料將範本分類，並且定義中顯示的方式**新專案**或**加入新項目** 對話方塊。|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定範本的內容。|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|選擇性項目。|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|選擇性項目。|  
  
### <a name="parent-elements"></a>父項目  
 無。  
  
## <a name="remarks"></a>備註  
 `VSTemplate`項目是.vstemplate 檔案的根項目。  
  
## <a name="example"></a>範例  
 下列範例會顯示專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式。  
  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)