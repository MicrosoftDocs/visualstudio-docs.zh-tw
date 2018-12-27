---
title: 專案項目 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19374e37f295b6d344b2c0f3991109371b1f4454
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561771"
---
# <a name="project-element-visual-studio-templates"></a>專案項目 （Visual Studio 範本）
指定要加入至專案目錄的檔案。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>語法  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`File`|必要屬性。<br /><br /> 在範本中指定的專案檔名稱 *.zip*檔案。|  
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定專案檔是否有從範本建立專案時，必須被取代的參數值。 預設值為 `false`。|  
|`TargetFileName`|選擇性屬性。<br /><br /> 從範本建立專案時，請指定專案檔的名稱。|  
|`IgnoreProjectParameter`|選擇性屬性。<br /><br /> 指定專案是否應新增至目前的方案。 如果自訂參數的值"$*myCustomParameter*$」 存在專案是在參數取代檔案中，建立，但未加入目前開啟的方案的一部分。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[資料夾](../extensibility/folder-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定要加入至專案的資料夾。|  
|[專案項目](../extensibility/projectitem-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定要加入至專案的檔案。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要項目。|  
  
## <a name="remarks"></a>備註  
 `Project` 是 `TemplateContent` 的選擇性子項目。  
  
 `Project`項目是用來指定專案，因此，僅在專案範本中無效。  
  
 `Project` 項目可以有[資料夾](../extensibility/folder-element-visual-studio-project-templates.md)子系項目或[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)子系項目，但兩者的混合`Folder`和`ProjectItem`子系項目。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動重新命名使用者所輸入的名稱為基礎的專案檔名**新的專案** 對話方塊。 使用`TargetFileName`屬性如果您想要提供使用範本建立的專案檔的替代檔案名稱。  
  
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
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 項目 （Visual Studio 專案範本）](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder 元素 （Visual Studio 專案範本）](../extensibility/folder-element-visual-studio-project-templates.md)