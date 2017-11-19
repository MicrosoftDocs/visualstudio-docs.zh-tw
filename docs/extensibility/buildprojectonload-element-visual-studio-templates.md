---
title: "BuildProjectOnload 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 362dd868e6f9c273e9495295a453d8da4e2183cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>BuildProjectOnload 項目 (Visual Studio 樣板)
當您建立並將其加入至方案，請建置新的專案。 不會建置整個方案。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<BuildProjectOnLoad >  
  
## <a name="syntax"></a>語法  
  
```vb  
<BuildProjectOnLoad> true/false </BuildOnLoad>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|TemplateData|將範本分類，以及定義它如何出現在同時**新專案**和**加入新項目**對話方塊。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字必須`true`或`false`用以表示是否要從範本建立時建立新的專案。  
  
## <a name="remarks"></a>備註  
 `BuildProjectOnLoad` 是選擇性項目。 預設值是 `false`。  
  
## <a name="example"></a>範例  
 下列範例會說明 Visual C# 範本的中繼資料。  
  
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
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)