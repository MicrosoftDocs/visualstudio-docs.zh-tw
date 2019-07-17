---
title: ProjectSubType 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d07a62027b494242d3c25aba00fbd5f4d75df78b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193895"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將範本分類的子類別目錄中指定的值為`ProjectType`項目。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType>  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 這個值會指定範本的子類別。  
  
## <a name="remarks"></a>備註  
 `ProjectSubType` 是 `TemplateData` 的選擇性子項目。  
  
 `ProjectSubType`項目會提供子類別目錄[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)項目。 這個值可以包含：  
  
- `SmartDevice-NETCFv1`：指定範本的目標[!INCLUDE[Compact](../includes/compact-md.md)]1.0 版。  
  
- `SmartDevice-NETCFv2`：指定 tempalate 目標[!INCLUDE[Compact](../includes/compact-md.md)]2.0 版。  
  
  如果範本中包含`ProjectType`值的項目`Web`，則`ProjectSubType`項目會指定範本的程式設計語言。 這個項目可以有下列值：  
  
- `CSharp`：指定此範本會建立[!INCLUDE[csprcs](../includes/csprcs-md.md)]Web 專案或項目。  
  
- `VisualBasic`：指定此範本會建立[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Web 專案或項目。  
  
## <a name="example"></a>範例  
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]裝置應用程式目標[!INCLUDE[Compact](../includes/compact-md.md)]2.0 版。  
  
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
