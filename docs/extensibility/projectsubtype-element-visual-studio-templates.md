---
title: 專案子類型元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701837"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>專案子型別元素(視覺化工作室範本)
將範本類別為`ProjectType`元素中指定值的子類別。

 \<VStemplate>\<範本資料>\<專案子類型>

## <a name="syntax"></a>語法

```xml
<ProjectSubType> SubType </ProjectSubType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此值指定範本的子類別。

## <a name="remarks"></a>備註
 `ProjectSubType` 是 `TemplateData` 的選擇性子項目。

 該`ProjectSubType`元素為[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)元素提供子類別。 這個值可以包括:

- `SmartDevice-NETCFv1`:指定範本以[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]版本 1.0 為目標。

- `SmartDevice-NETCFv2`:指定範本以[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]版本 2.0 為目標。

  如果範本包含`ProjectType`的值的元素`Web`,`ProjectSubType`則元素指定範本的程式設計語言。 此元素可以具有以下值:

- `CSharp`:指定範本建立[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Web 專案或項。

- `VisualBasic`:指定範本建立[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Web 專案或項。

## <a name="example"></a>範例
 下面的範例顯示了針對版本 2.0[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]的裝置應用程式的專案樣本[!INCLUDE[Compact](../extensibility/includes/compact_md.md)]的元資料。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [專案類型元素(視覺化工作室範本)](../extensibility/projecttype-element-visual-studio-templates.md)
