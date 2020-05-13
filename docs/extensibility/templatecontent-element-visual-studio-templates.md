---
title: 範本內容元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699226"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent 項目 (Visual Studio 範本)

指定範本的內容。

元素層次結構:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>語法

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|指定是否從範本創建專案時生成解決方案。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定多專案範本的組織和內容。|
|[專案](../extensibility/project-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定要新增到專案的檔案或目錄。|
|[參考](../extensibility/references-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定專案範本所需的程式集引用。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|選擇性項目。<br /><br /> 指定樣本中包含的檔。|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定從範本建立項目或專案時要使用的任何自訂參數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要元素。<br /><br /> 包含專案範本、專案範本或初學者工具組的所有元資料。|

## <a name="remarks"></a>備註
 `TemplateContent`是必需的元素。

## <a name="example"></a>範例
 下面的範例顯示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式的專案範本的元數據。

```xml
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
            <ProjectItem>Form1.cs</ProjectItem>
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

- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
