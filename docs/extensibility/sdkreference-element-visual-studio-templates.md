---
title: " (Visual Studio 範本的 SDKReference 元素) |Microsoft Docs"
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f43c813e688c1e175f1d36e6f06125f92404c48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700169"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference 項目 (Visual Studio 樣板)
指定項目範本使用 SDK 參考。

## <a name="syntax"></a>語法

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

|項目|描述|
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
