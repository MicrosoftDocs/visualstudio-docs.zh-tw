---
title: 專案元素(可視化工作室專案範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701867"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem 項目 (Visual Studio 項目範本)
指定項目範本中包含的檔。

> [!NOTE]
> 元素`ProjectItem`接受不同的屬性,具體取決於範本是針對項目還是項。 本主題介紹專案`ProjectItem`的元素。 有關專案範本`ProjectItem`元素的說明,請參閱[ProjectItem 元素(可視化工作室專案範本)。](../extensibility/projectitem-element-visual-studio-project-templates.md)

 \<>项目项目\<>>\<的「範本」>模板内容

## <a name="syntax"></a>語法

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
| `SubType` | 選擇性屬性。<br /><br /> 指定多檔項目樣本中項目的子類型。 此值用於確定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]將用於打開項的編輯器。 |
| `CustomTool` | 選擇性屬性。<br /><br /> 為專案檔中的項設置自定義工具。 |
| `ItemType` | 選擇性屬性。<br /><br /> 設置專案檔中項的物料類型。 |
| `ReplaceParameters` | 選擇性屬性。<br /><br /> 布爾值,用於指定項是否具有從範本創建項目時必須替換的參數值。 預設值為 `false`。 |
| `TargetFileName` | 選擇性屬性。<br /><br /> 指定從範本建立的項目名稱。 此屬性可用於使用參數替換創建項名稱。 |

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|

## <a name="text-value"></a>文字值
 需要文字值。

 表示`string`樣本 *.zip*檔案中檔案名稱的 。

## <a name="remarks"></a>備註
 `ProjectItem`是`TemplateContent`的可選子項。

 該`TargetFileName`屬性可用於重命名具有參數的檔。 例如,如果檔案*MyFile.vb*存在於樣本 *.zip*檔案的根目錄中,但您希望根據使用者在 **'新增新項目'** 對話框中的檔案名命名該檔案,則可以使用以下 XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 使用此範本建立專案時,檔名將基於使用者在「**添加新項目**」對話框中輸入的名稱。 這在創建多檔項範本時非常有用。 關於詳細資訊,請參閱[如何:建立多檔項目樣本](../ide/how-to-create-multi-file-item-templates.md)與[樣本參數](../ide/template-parameters.md)。

## <a name="example"></a>範例
 下面的範例演示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類的標準項範本的元數據。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
- [如何：建立多檔案項目範本](../ide/how-to-create-multi-file-item-templates.md)
- [範本參數](../ide/template-parameters.md)
