---
title: Icon 元素 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 145974e3e9eefd92f052940834079ad05f3d3849
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013919"
---
# <a name="icon-element-visual-studio-templates"></a>Icon 元素 （Visual Studio 範本）
指定的路徑和檔名做為圖示時，就會出現在其中一個映像檔的**新的專案**或**加入新項目**對話方塊中，範本。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<圖示 >  
  
## <a name="syntax"></a>語法  
  
```  
<Icon>  
    IconFileName  
</Icon>  
```  
  
```  
<Icon Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Package`|選擇性屬性，為進階的使用者案例。<br /><br /> 指定 Visual Studio 套件的 GUID 識別碼。|  
|`ID`|選擇性屬性，為進階的使用者案例。<br /><br /> 指定 Visual Studio 資源識別碼。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要的文字值，除非`Package`和`ID`屬性使用。  
  
 文字提供的路徑和檔案名稱會出現在 範本 圖示**新的專案** 對話方塊。  
  
## <a name="remarks"></a>備註  
 `Icon` 是 `TemplateData` 的必要子項目。  
  
## <a name="example"></a>範例  
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案與項目範本](../ide/creating-project-and-item-templates.md)