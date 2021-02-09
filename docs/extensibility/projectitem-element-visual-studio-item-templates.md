---
title: 專案範本 (Visual Studio 專案範本) |Microsoft Docs
description: 瞭解專案範本的 [專案專案] 元素，以及它如何接受不同的屬性，取決於範本是針對專案或專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 201f6e7845f1294892836de4cca24195fb0f1596
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928233"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem 項目 (Visual Studio 項目範本)
指定包含在專案範本中的檔案。

> [!NOTE]
> `ProjectItem`專案會根據範本是針對專案或專案而接受不同的屬性。 本主題說明 `ProjectItem` 專案的元素。 如需 `ProjectItem` 專案範本專案的說明，請參閱 [專案範本 (Visual Studio 專案範本的 [專案] 元素) ](../extensibility/projectitem-element-visual-studio-project-templates.md)。

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
|---------------------| - |
| `SubType` | 選擇性屬性。<br /><br /> 指定多檔案專案範本中專案的子類型。 此值可用來判斷 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 將用來開啟專案的編輯器。 |
| `CustomTool` | 選擇性屬性。<br /><br /> 設定專案檔中專案的 CustomTool。 |
| `ItemType` | 選擇性屬性。<br /><br /> 設定專案檔中專案的 ItemType。 |
| `ReplaceParameters` | 選擇性屬性。<br /><br /> 布林值，指定專案是否有在從範本建立專案時必須取代的參數值。 預設值為 `false`。 |
| `TargetFileName` | 選擇性屬性。<br /><br /> 指定從範本建立之專案的名稱。 這個屬性適用于使用參數取代來建立專案名稱。 |

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|

## <a name="text-value"></a>文字值
 需要文字值。

 `string`，表示範本 *.zip* 檔中的檔案名。

## <a name="remarks"></a>備註
 `ProjectItem` 是的選擇性子系 `TemplateContent` 。

 `TargetFileName`屬性可以用來以參數重新命名檔案。 例如，如果檔案 *myfile.txt* 是存在於範本 *.zip* 檔案的根目錄中，但您想要根據使用者在 [ **加入新專案** ] 對話方塊中提供的檔案名來命名檔案，您可以使用下列 XML：

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 從這個範本建立專案時，檔案名會根據使用者在 [ **加入新專案** ] 對話方塊中輸入的名稱。 這在建立多檔案專案範本時很有用。 如需詳細資訊，請參閱 [如何：建立多檔案專案範本](../ide/how-to-create-multi-file-item-templates.md) 和 [範本參數](../ide/template-parameters.md)。

## <a name="example"></a>範例
 下列範例說明類別標準專案範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)
- [範本參數](../ide/template-parameters.md)
