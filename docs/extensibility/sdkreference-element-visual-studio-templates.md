---
title: " (Visual Studio 範本的 SDKReference 元素) |Microsoft Docs"
description: 瞭解 SDKReference 元素，以及它如何指定專案範本使用 SDK 參考。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ab748a309bf57af79753596ede11b371589faa8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941559"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference 項目 (Visual Studio 樣板)
指定項目範本使用 SDK 參考。

## <a name="syntax"></a>Syntax

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[參考](../extensibility/reference-element-visual-studio-templates.md)|指定項目加入專案時要加入的組件參考。|

## <a name="text-value"></a>文字值
 需要文字值。

## <a name="remarks"></a>備註
 這個文字會指定在具現化項目範本時，將 SDK 參考加入專案。

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>另請參閱
- [References 元素 (Visual Studio 範本)](../extensibility/references-element-visual-studio-templates.md)
- [Reference 元素 (Visual Studio 範本)](../extensibility/reference-element-visual-studio-templates.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
