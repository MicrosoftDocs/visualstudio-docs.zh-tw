---
title: 建立位置元素(視覺化工作室範本)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab2b5d68be069f30c8f71536b6d47cb1ce8823b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739656"
---
# <a name="createinplace-element-visual-studio-templates"></a>建立 InPlace 元素(視覺化工作室樣本)
指定是在指定位置建立專案並執行參數替換,還是在臨時位置執行參數替換,然後將專案保存到指定位置。

 \<vstemplate>\<範本資料>\<創建原>

## <a name="syntax"></a>語法

```
<CreateInPlace> true/false </CreateInPlace>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字必須是 `true` 或 `false`。 如果`true`創建專案並在 **「新專案」** 對話方塊中指定的位置執行參數替換。 如果在`false`暫時位置執行 參數替換,然後將專案複製到指定位置。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `true`。

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
        <CreateInPlace>false</CreateInPlace>
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
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
