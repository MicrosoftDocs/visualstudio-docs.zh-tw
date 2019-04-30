---
title: NumberOfParentCategoriesToRollUp 項目 （Visual Studio 範本）
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b733b65a62db3cb39197fbdbed4c471651eae49a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433639"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp 項目 （Visual Studio 範本）
指定的數目會顯示在範本的父類別**新的專案** 對話方塊。

 \<VSTemplate> \<TemplateData> \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>語法

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 `integer`是必要的值。

 這個值會指定將會顯示在範本的父類別的數目**新的專案** 對話方塊。

## <a name="remarks"></a>備註
 `NumberOfParentCategoriesToRollUp` 是選擇性項目。

## <a name="example"></a>範例
 此範例說明的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows 應用程式。 如果此中繼資料的範本放兩個資料夾層級以下的最上層[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]節點，此範本將顯示在中的最上層節點**新的專案** 對話方塊。 如果`NumberOfParentCategoriesToRollUp`未設定，範本只會出現在節點中實際上是位於。

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)