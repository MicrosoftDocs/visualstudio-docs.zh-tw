---
title: " (Visual Studio 範本的 AppliesTo 元素) |Microsoft Docs"
description: 深入瞭解 AppliesTo 元素，以及它如何指定選擇性運算式來比對一或多項功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 340ac4db04b62abade9c6572335e28c9fb27b495
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097470"
---
# <a name="appliesto-element-visual-studio-templates"></a> (Visual Studio 範本的 AppliesTo 元素) 

指定選用的運算式來比對一或多項功能 (查看 <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>) 。 功能是由專案類型透過階層公開為屬性 [__VSHPROPID5。VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>)。 如此一來，範本就可以在具有通用功能的多個專案類型之間共用。

這是選擇性的項目。 一個範本檔最多只能有一個執行個體。 這個項目只會根據目前選取的現用專案，讓項目範本加入成為適用的範本。 它不能用來讓項目範本變成不適用。 如果 `AppliesTo` 不存在或運算式未成功選擇加入，則會使用 `TemplateID` 或 `TemplateGroupID` 讓範本成為適用，就如舊版產品一樣。

已在 Visual Studio 2013 Update 2 中引入。 若要參考正確的版本，請參閱 [VISUAL STUDIO 2013 SDK Update 2 中提供的參考元件](/previous-versions/dn632168(v=vs.120))。

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntax

```xml
<AppliesTo>Capability1</AppliesTo>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類。|

## <a name="text-value"></a>文字值

需要文字值。 此文字會指定專案的功能。

有效的運算式語法定義如下：

- 功能運算式，例如 " (VisualC &#124; CSharp) + (MSTest &#124; NUnit) 」。

- "&#124;" 是 OR 運算子。

- "&" 和 "+" 字元都是和運算子。

- "!" 字元是 NOT 運算子。

- 括號會強制執行評估優先順序。

- Null 或空白運算式會判斷值為相符項目。

- 專案功能可以是下列保留字元以外的任何字元： "' '：;，+-*/ \\ ！ ~&#124;&% $ @ ^ () = {} [] <>？ \t\b\n\r

## <a name="example"></a>範例

下列範例將示範三個不同的範本。 `Template1` 適用于所有 c # 專案類型或任何其他支援此功能的專案類型 `WindowsAppContainer` 。 `Template2` 適用于任何種類的 c # 專案。 `Template3` 適用於不是 `WindowsAppContainer` 專案的 C# 專案。

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
