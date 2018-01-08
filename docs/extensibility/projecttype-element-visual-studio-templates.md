---
title: "ProjectType 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords: ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 46f9f748f683558e6fb82607d4c87a0a0dbc1cae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType 項目 (Visual Studio 範本)
將專案範本分類，使其出現在中指定的群組**新專案**或**加入新項目** 對話方塊。  
  
> [!WARNING]
>  啟動 Visual Studio 2012 中的 c + + 支援專案範本。 不支援 c + + 在 Visual Studio 2010 和舊版中。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
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
  
 這個值會指定的專案範本類型將會建立，而且必須包含下列值之一：  
  
-   `CSharp`： 指定這個範本會建立[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]專案或項目。  
  
-   `VisualBasic`： 指定這個範本會建立[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]專案或項目。  
  
-   `Web`： 指定此範本建立 Web 專案或項目。 如果`ProjectType`項目包含此值，語言的專案或項目會定義在[ProjectSubType 項目 （Visual Studio 範本）](../extensibility/projectsubtype-element-visual-studio-templates.md)。  
  
## <a name="remarks"></a>備註  
 `ProjectType` 是 `TemplateData` 的必要子項目。  
  
 值`ProjectType`項目會指定範本所在**新專案**或**加入新項目** 對話方塊。 比方說，與範本`ProjectType`值`CSharp`之下**Visual C#**中的節點**新專案**對話方塊。  
  
 範本子類型可以指定使用[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)項目。  
  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType 元素 (Visual Studio 範本)](../extensibility/projectsubtype-element-visual-studio-templates.md)