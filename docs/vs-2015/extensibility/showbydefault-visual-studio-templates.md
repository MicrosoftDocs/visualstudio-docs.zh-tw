---
title: ShowByDefault （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 063836d07931456d99bce31c793866e7d5421c91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486753"
---
# <a name="showbydefault-visual-studio-templates"></a>ShowByDefault (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ShowByDefault （Visual Studio 範本）](https://docs.microsoft.com/visualstudio/extensibility/showbydefault-visual-studio-templates)。  
  
如果`false`，指定範本只會顯示在指定[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ShowByDefault >  
  
## <a name="syntax"></a>語法  
  
```  
<ShowByDefault> true/false </ShowByDefault>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此文字必須是 `true` 或 `false`。 如果為 true，請指定範本將會針對所有專案類型顯示。 如果為 false，則範本只會顯示在指定的 `TemplateGroupID` 之下。  
  
## <a name="remarks"></a>備註  
 `ShowByDefault` 是選擇性項目。 預設值是 `true`。  
  
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
        <ShowByDefault>false</ShowByDefault>  
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
 [TemplateGroupID 元素 (Visual Studio 範本)](../extensibility/templategroupid-element-visual-studio-templates.md)

