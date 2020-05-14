---
title: 啟用位置欄位元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e15e2f5c070b8a8c565497c6ba3fc6490b87591
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711997"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>開啟位置位置元素(視覺化工作室樣本)
指定使用者是否可以編輯位置欄位。

 \<VStemplate>\<範本資料>\<啟用定位欄位>

## <a name="syntax"></a>語法

```
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 None

### <a name="child-elements"></a>子元素
 None

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須為`true``false`或 ,指示使用者是否可以編輯 **「新項目**」對話方塊上**的位置文字**框。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值為`true`,允許使用者在 **「新項目」** 對話方塊中的 **「位置**」文字框中編輯該值。

 在"**新項目**"對話框中,"**位置**「文字框指定儲存新項目的目錄。

## <a name="example"></a>範例
 下面的範例演示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows應用程式的中繼資料。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableEditOfLocationField>false</EnableEditOfLocationField>
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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
