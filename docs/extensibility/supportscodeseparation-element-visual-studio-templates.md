---
title: SupportsCodeSeparation 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 504e176973cd9bb6f0041254e0de19d675be05df
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716463"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation 項目 (Visual Studio 範本)
指定是否**程式碼置於個別的檔案**中已啟用 核取方塊**加入新項目** 對話方塊。

 \<VSTemplate> \<TemplateData> \<SupportsCodeSeparation>

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

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義中顯示的方式**新的專案**或**新項目**對話方塊。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是`true`或`false`，這表示，zda bude**程式碼置於個別檔案**中已啟用 核取方塊**加入新項目** 對話方塊。

## <a name="remarks"></a>備註
 `SupportsCodeSeparation` 是選擇性項目。 預設值為 `false`。

 `SupportsCodeSeparation`項目僅適用於 Web 項目範本。

 程式碼分離或程式碼後置頁面模型中，可讓您將標記放在一個檔案，將程式碼放在另一個檔案。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 和其他.NET 語言使用此模型。

## <a name="example"></a>範例
 下列範例會指定要顯示**程式碼置於個別檔案**選項。

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