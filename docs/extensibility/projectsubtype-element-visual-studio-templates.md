---
title: ProjectSubType 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4414d5f444613996312978e9033145c6b8d3d82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138996"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType 項目 (Visual Studio 範本)
將範本分類的子類別目錄中指定的值為`ProjectType`項目。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 這個值會指定範本的子類別。  
  
## <a name="remarks"></a>備註  
 `ProjectSubType` 是 `TemplateData` 的選擇性子項目。  
  
 `ProjectSubType`項目會提供以子類別[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)項目。 這個值可以包含：  
  
-   `SmartDevice-NETCFv1`： 指定範本的目標[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]1.0 版。  
  
-   `SmartDevice-NETCFv2`： 指定 tempalate 目標[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]2.0 版。  
  
 如果範本包含`ProjectType`值的項目`Web`、`ProjectSubType`項目會指定範本的程式設計語言。 這個項目可以是下列值：  
  
-   `CSharp`： 指定這個範本會建立[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Web 專案或項目。  
  
-   `VisualBasic`： 指定這個範本會建立[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Web 專案或項目。  
  
## <a name="example"></a>範例  
 下列範例會顯示專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]裝置應用程式目標[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]2.0 版。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectType 元素 (Visual Studio 範本)](../extensibility/projecttype-element-visual-studio-templates.md)