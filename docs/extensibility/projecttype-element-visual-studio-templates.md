---
title: 項目類型元素(視覺工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701800"
---
# <a name="projecttype-element-visual-studio-templates"></a>專案類型元素(視覺化工作室範本)
對專案範本進行分類,使其顯示在 **「新專案**」或 **「新增新專案」** 對話方塊中的指定群組下。

> [!WARNING]
> 支援在 Visual Studio 2012 中啟動C++範本。 在 Visual Studio 2010 和早期版本中,C++不支援它們。

 \<樣本>\<範本資料>\<專案類型>

## <a name="syntax"></a>語法

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 這個值指定範本將建立的項目類型,並且必須包含以下值之一:

- `CSharp`指定樣本建立[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]項目或項。

- `VisualBasic`指定樣本建立[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]項目或項。

- `Web`:指定範本建立 Web 專案或項。 如果`ProjectType`元素包含此值,則專案或項目的語言會定義在[ProjectSubType 元素(視覺化工作室樣本)中](../extensibility/projectsubtype-element-visual-studio-templates.md)。

## <a name="remarks"></a>備註
 `ProjectType` 是 `TemplateData` 的必要子項目。

 `ProjectType`元素的值指定範本在 **「新專案**」或 **「新增新項目**」對話框中的位置。 例如,在 **「新項目**」對話`ProjectType`框`CSharp`中的 **「可視化 C#」** 節點下,將顯示值為的範本。

 可以使用[Project SubType](../extensibility/projectsubtype-element-visual-studio-templates.md)元素指定範本子類型。

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
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [專案子型別元素(視覺化工作室範本)](../extensibility/projectsubtype-element-visual-studio-templates.md)
