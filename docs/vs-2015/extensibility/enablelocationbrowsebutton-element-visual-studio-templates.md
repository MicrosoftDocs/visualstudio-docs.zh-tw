---
title: EnableLocationBrowseButton 元素 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04d5710012840079e3381f09725b96b8f329872d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795735"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定是否**瀏覽** 按鈕位於**新的專案**對話方塊，讓使用者可以輕鬆地修改儲存新專案的預設目錄。  
  
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
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字必須是`true`或`false`，指出是否要顯示**瀏覽**按鈕**新專案** 對話方塊。  
  
## <a name="remarks"></a>備註  
 `EnableLocationBrowseButton` 是選擇性項目。 預設值是`true`，以顯示**瀏覽**按鈕**新專案** 對話方塊。  
  
 在 [**新的專案**] 對話方塊中，**位置**文字方塊指定儲存新專案的目錄。 **瀏覽** 按鈕可協助您修改所顯示的這個目錄**專案位置**對話方塊中，可讓您輕鬆地瀏覽至不同的目錄，可從您的電腦，以及然後選擇它做為儲存新的專案目錄。  
  
## <a name="example"></a>範例  
 下列範例說明的中繼資料[!INCLUDE[csprcs](../includes/csprcs-md.md)]Windows 應用程式。  
  
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

