---
title: " (Visual Studio 範本的參考元素) |Microsoft Docs"
description: 瞭解參考專案，以及它如何指定將專案加入至專案時所要加入的元件參考。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fc23edf0897ca71f1b59f126987e42f9d3cb1a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068514"
---
# <a name="reference-element-visual-studio-templates"></a> (Visual Studio 範本的參考元素) 
指定項目加入專案時要加入的組件參考。

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

## <a name="syntax"></a>Syntax

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[組件](../extensibility/assembly-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定元件的相關資訊，範本會使用此元件將該元件的參考加入至專案。 `Assembly`每個元素中都必須有一個元素 `Reference` 。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[參考](../extensibility/references-element-visual-studio-templates.md)|將範本加入至專案的元件參考組成群組。|

## <a name="remarks"></a>備註
 `Reference` 是 `References` 的必要子項目。

 `Reference`和 `References` 元素只能用在具有屬性值的 .vstemplate 檔案中。 `Type` `Item`

## <a name="example"></a>範例
 下列範例說明 `TemplateContent` 專案範本的元素。 這個 XML 會將參考加入 *System.dll* 和 *System.Data.dll* 元件。

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
