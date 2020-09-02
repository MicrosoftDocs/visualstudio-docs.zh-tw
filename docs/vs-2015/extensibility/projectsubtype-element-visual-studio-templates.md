---
title: " (Visual Studio 範本的 ProjectSubType 元素) |Microsoft Docs"
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193895"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

將範本分類為元素中指定之值的子類別 `ProjectType` 。  
  
 \<VSTemplate>  
 \<TemplateData>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 此值會指定範本的子類別。  
  
## <a name="remarks"></a>備註  
 `ProjectSubType` 是 `TemplateData` 的選擇性子項目。  
  
 `ProjectSubType`元素提供[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)專案的子類別。 此值可包含：  
  
- `SmartDevice-NETCFv1`：指定以1.0 版為目標的範本 [!INCLUDE[Compact](../includes/compact-md.md)] 。  
  
- `SmartDevice-NETCFv2`：指定 tempalate 以 [!INCLUDE[Compact](../includes/compact-md.md)] 2.0 版為目標。  
  
  如果範本包含 `ProjectType` 值為的元素 `Web` ， `ProjectSubType` 元素會指定範本的程式設計語言。 這個元素可以有下列值：  
  
- `CSharp`：指定範本建立 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Web 專案或專案。  
  
- `VisualBasic`：指定範本建立 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Web 專案或專案。  
  
## <a name="example"></a>範例  
 下列範例顯示以 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 2.0 版為目標之裝置應用程式的專案範本中繼資料 [!INCLUDE[Compact](../includes/compact-md.md)] 。  
  
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
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和專案範本](../ide/creating-project-and-item-templates.md)   
 [ProjectType 元素 (Visual Studio 範本)](../extensibility/projecttype-element-visual-studio-templates.md)
