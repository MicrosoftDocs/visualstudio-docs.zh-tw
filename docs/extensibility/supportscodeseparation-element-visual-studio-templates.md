---
title: 支援代碼分離元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd52ae47f47f3ca1fce23f7cf8d37260ec86fb0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699503"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation 項目 (Visual Studio 範本)
在 **「新增新項目**」對話框中指定是否啟用**了單獨檔中的放置代碼**複選框。

 \<樣本>\<範本資料>\<支援代碼分離>

## <a name="syntax"></a>語法

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 對樣本進行分類,並定義範本在 **「新專案**」或「**新項目**」對話框中的顯示方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須為或`true``false`,指示在 **'新增新項目**'對話框中是否啟用**了一個檔案複選框中的放置代碼**。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `false`。

 該`SupportsCodeSeparation`元素僅適用於 Web 項範本。

 代碼分離或代碼背後的頁面模型允許您將標記保存在一個檔中,而程式設計代碼儲存在另一個檔中。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]和其他 .NET 語言使用此模型。

## <a name="example"></a>範例
 下面的範例指定在**單獨的檔案選項中**顯示 Place 代碼。

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
