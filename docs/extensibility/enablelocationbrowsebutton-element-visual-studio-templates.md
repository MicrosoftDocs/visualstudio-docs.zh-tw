---
title: EnableLocationBrowseButton 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d3573a1359cf7cc6347ede28b5361b01bbb7efb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126841"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton 項目 (Visual Studio 範本)
指定是否**瀏覽**按鈕位於**新專案**對話方塊，讓使用者可以輕鬆地修改儲存新專案的預設目錄。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<EnableLocationBrowseButton >  
  
## <a name="syntax"></a>語法  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
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
  
 文字必須是`true`或`false`，指出是否顯示**瀏覽**按鈕**新專案** 對話方塊。  
  
## <a name="remarks"></a>備註  
 `EnableLocationBrowseButton` 是選擇性項目。 預設值是`true`，用來顯示**瀏覽**按鈕**新專案** 對話方塊。  
  
 在**新專案**對話方塊中，**位置**文字方塊中指定儲存新專案的目錄。 **瀏覽**按鈕可協助您修改這個目錄顯示**專案位置**對話方塊，可讓您輕鬆地巡覽至其他目錄，可從您的電腦，並然後選擇它以儲存新專案的目錄。  
  
## <a name="example"></a>範例  
 下列範例說明的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows 應用程式。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)