---
title: LocationField 項目 （Visual Studio 專案範本） |Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea66808097c0e62d6c36781d7f288ed06975f6e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491925"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField 項目 (Visual Studio 專案範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[LocationField 項目 （Visual Studio 專案範本）](https://docs.microsoft.com/visualstudio/extensibility/locationfield-element-visual-studio-project-templates)。  
  
指定是否**位置**中的文字方塊**新的專案** 對話方塊中已啟用、 停用，或隱藏專案範本。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<LocationField >  
  
## <a name="syntax"></a>語法  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義中顯示的方式**新的專案**。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 有效的文字值如下：  
  
-   `Enabled`其中指定**位置**的方塊**新的專案** 對話方塊中已啟用。  
  
-   `Disabled`其中指定**位置**的方塊**新的專案** 對話方塊中已停用。  
  
-   `Hidden`其中指定**位置**的方塊**新的專案**隱藏的對話方塊。  
  
## <a name="remarks"></a>備註  
 預設值是 `Enabled`。  
  
 **位置**中的文字方塊**新的專案**對話方塊可讓使用者能夠變更已儲存新專案的預設目錄。  
  
 中指定的值`Location`項目才會接受對話方塊如果基礎專案系統支援它。  
  
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
        <LocationField>Disabled</LocationField>  
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

