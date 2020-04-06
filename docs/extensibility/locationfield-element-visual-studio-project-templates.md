---
title: 位置欄位元素(可視化工作室專案範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702890"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>位置欄位元素(視覺化工作室專案樣本)
指定新**項目**對話框中**的位置**文字框是為專案範本啟用、禁用還是隱藏。

 \<VS範本>\<範本資料>\<位置欄位>

## <a name="syntax"></a>語法

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 對樣本進行分類,並定義它在「**新專案**」中的顯示方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 合法文字值為:

- `Enabled`,它指定啟用 **"新專案"** 對話方**塊的位置**框。

- `Disabled`,它指定禁用 **"新專案"** 對話方**塊的位置**框。

- `Hidden`指定新**項目**對話框的位置**框**為隱藏。

## <a name="remarks"></a>備註
 預設值是 `Enabled`。

 "**新的項目**'對話框中的 **'位置**"文字框使用戶能夠更改儲存新項目的預設目錄。

 僅當基礎項目系統支援`Location`該元素時,對話方塊才會遵守元素中指定的值。

## <a name="example"></a>範例
 下列範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範本的中繼資料。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
