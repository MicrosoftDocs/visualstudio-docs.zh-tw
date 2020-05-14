---
title: 專案元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701996"
---
# <a name="project-element-visual-studio-templates"></a>專案元素(可視化工作室範本)
指定要新增到專案的檔案或目錄。

 \<VStemplate \<\<>模板内容>项目>

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
|`File`|必要屬性。<br /><br /> 在樣本 *.zip*檔案中指定專案檔的名稱。|
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布爾值,用於指定專案檔是否具有從範本創建專案時必須替換的參數值。 預設值為 `false`。|
|`TargetFileName`|選擇性屬性。<br /><br /> 指定從範本建立專案時的專案檔的名稱。|
|`IgnoreProjectParameter`|選擇性屬性。<br /><br /> 指定是否應將專案添加到當前解決方案。 如果自定義參數的值 *「$myCustom 參數*$」存在於參數替換檔中,則專案將創建,但不會作為當前打開的解決方案的一部分添加。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[資料夾](../extensibility/folder-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定要新增到項目的資料夾。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定要加入項目的檔案。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要元素。|

## <a name="remarks"></a>備註
 `Project` 是 `TemplateContent` 的選擇性子項目。

 該`Project`元素用於指定專案,因此僅在專案範本中有效。

 `Project`元素可以具有[資料夾](../extensibility/folder-element-visual-studio-project-templates.md)子元素或[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)子元素,但不能混合`Folder`兩`ProjectItem`個子 元素和子元素。

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]根據使用者在 **「新項目**」對話框中輸入的名稱自動重新命名專案檔名。 如果要為`TargetFileName`使用範本創建的專案檔提供備用檔名,請使用該屬性。

## <a name="example"></a>範例
 下面的範例顯示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式的專案範本的元數據。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
- [專案項目元素(可視化工作室專案範本)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [資料夾元素(視覺化工作室專案樣本)](../extensibility/folder-element-visual-studio-project-templates.md)
