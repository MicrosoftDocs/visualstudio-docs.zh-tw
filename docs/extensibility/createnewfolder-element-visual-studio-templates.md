---
title: 建立新資料夾元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 860f4df3e69a568a3e391da4d7437d9a5fd83f15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739678"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>建立新資料夾元素(視覺化工作室範本)
決定是否要檢查建立專案的目標目錄是否不存在。 如果目錄不存在，則可為專案建立全新的目錄。 此設定通常會由 `NewProjectRequiresNewFolder(VsTemplate)` 登錄旗標 (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`) 覆寫，所有一般專案類型都會使用此設定來決定是否要在新目錄中建立新專案。

 \<樣本>\<樣本資料>\<創建新資料夾>

## <a name="syntax"></a>語法

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>類型
 `Boolean`

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是 `true` 或 `false`，表示是否應該在從範本建立專案時建立新的容器資料夾。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `true`。

 僅在基礎專案系統支援時，`CreateNewFolder` 才會接受在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 項目中指定的值。

## <a name="example"></a>範例
 下列程式碼範例指定從範本建立專案時，不要建立新資料夾。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
