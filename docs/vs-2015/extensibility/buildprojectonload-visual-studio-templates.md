---
title: BuildProjectOnLoad (Visual Studio 範本) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- <BuildOnLoad> element [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 209f015103a291940f2d43ccdbfd140d71c9e8ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184607"
---
# <a name="buildprojectonload-visual-studio-templates"></a>BuildProjectOnLoad (Visual Studio 樣板)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定是否要在建立專案之後立即建立專案。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<BuildProjectOnLoad>  
  
## <a name="syntax"></a>語法  
  
```  
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字必須是 `true` 或 `false` ，指出是否要在建立專案之後立即建立專案。  
  
## <a name="remarks"></a>備註  
 `BuildProjectOnLoad` 是選擇性屬性。 預設值是 `false`。  
  
## <a name="example"></a>範例  
 下列範例說明 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 範本的中繼資料。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <BuildProjectOnload>true</BuildProjectOnLoad>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [ (Visual Studio 範本的 TemplateContent 元素) ](../extensibility/templatecontent-element-visual-studio-templates.md)   
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
