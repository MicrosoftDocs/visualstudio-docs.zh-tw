---
title: NumberOfParentCategoriesToRollUp (Visual Studio 範本) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 278d8537ee253d8c79024d5e866befa1d65ded0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194206"
---
# <a name="numberofparentcategoriestorollup-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定將在 [ **新增專案** ] 對話方塊中顯示範本的父類別目錄數目。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<NumberOfParentCategoriesToRollUp>  
  
## <a name="syntax"></a>語法  
  
```  
<NumberOfParentCategoriesToRollUp>  
    1  
</NumberOfParentCategoriesToRollUp>  
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
 `integer`需要值。  
  
 這個值會指定要在 [ **新增專案** ] 對話方塊中顯示範本的父類別目錄數目。  
  
## <a name="remarks"></a>備註  
  是選擇性元素。  
  
## <a name="example"></a>範例  
 此範例說明 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows 應用程式的中繼資料。 如果具有此中繼資料的範本放在最上層節點下的兩個資料夾層級 [!INCLUDE[csprcs](../includes/csprcs-md.md)] ，則範本會出現在 [ **新增專案** ] 對話方塊的最上層節點中。 如果 `NumberOfParentCategoriesToRollUp` 未設定，則範本只會顯示在實體所在的節點上。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
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
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
