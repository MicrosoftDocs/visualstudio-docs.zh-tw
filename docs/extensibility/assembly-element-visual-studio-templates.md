---
title: 元件元素 (Visual Studio 範本) |Microsoft Docs
titleSuffix: ''
description: 瞭解 Assembly 元素，以及它如何指定元件的相關資訊，範本會使用此元件將該元件的參考加入至專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7891687a76d0023b54be2c44c3b5fc09c97f010
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932791"
---
# <a name="assembly-element-visual-studio-templates"></a>元件元素 (Visual Studio 範本) 
指定元件的相關資訊，範本會使用此元件將該元件的參考加入至專案。

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Syntax

```
<Assembly> AssemblyName </Assembly>
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
|[參考](../extensibility/reference-element-visual-studio-templates.md)|指定項目加入專案時要加入的組件參考。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字會指定當專案範本具現化時，要加入至專案的元件。 此元件名稱必須以下列其中一種方式指定：

- 作為完整元件名稱。 例如：

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- 做為簡單的文字參考。 例如：

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>備註
 `Assembly` 是 `Reference` 的必要子項目。

 `Reference`、 `References,` 和 `Assembly` 元素只能用在具有屬性值 *的 .vstemplate* 檔案中 `Type` `Item` 。

## <a name="example"></a>範例
 下列範例說明 `TemplateContent` 專案範本的元素。 這個 XML 會將參考加入 *System.dll* 和 *System.Data.dll* 元件。

```
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
