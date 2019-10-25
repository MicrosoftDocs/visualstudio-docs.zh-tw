---
title: SupportsCodeSeparation 元素（Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e68516a798bcd4d1437ab504c09b4cc529eb889
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719420"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation 項目 (Visual Studio 範本)
指定是否在 [**加入新專案**] 對話方塊中，啟用 [將程式**代碼放在不同**的檔案] 核取方塊。

 \<VSTemplate > \<TemplateData > \<SupportsCodeSeparation >

## <a name="syntax"></a>語法

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子項目
 無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義它在 [**新增專案**] 或 [**新增專案**] 對話方塊中的顯示方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字必須是 `true` 或 `false`，指出是否已在 [**加入新專案**] 對話方塊中啟用 [將程式**代碼放在不同**的檔案中] 核取方塊。

## <a name="remarks"></a>備註
 `SupportsCodeSeparation` 是選擇性項目。 預設值是 `false`。

 @No__t_0 元素僅適用于 Web 專案範本。

 程式碼分隔，或程式碼後置頁面模型可讓您將標記保留在一個檔案中，並將程式碼放在另一個檔案中。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 和其他 .NET 語言都會使用此模型。

## <a name="example"></a>範例
 下列範例會指定將位置程式**代碼顯示在不同的**檔案選項中。

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

## <a name="see-also"></a>請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)