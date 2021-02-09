---
title: " (Visual Studio 範本的 CustomParameters 元素) |Microsoft Docs"
description: 瞭解 CustomParameters 元素，以及當 wizard 進行參數取代時，如何將傳遞給範本嚮導的自訂參數分組。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a899790890bd299dcb77558d31499b0a61bcefe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927128"
---
# <a name="customparameters-element-visual-studio-templates"></a> (Visual Studio 範本的 CustomParameters 元素) 
當 wizard 進行參數取代時，將要傳遞給範本嚮導的自訂參數分組。

## <a name="syntax"></a>Syntax

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 包含從範本建立專案或專案時所要使用的自訂參數名稱和值。 `CustomParameter` 元素中可能有零個或多個 `CustomParameters` 元素。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|

## <a name="remarks"></a>備註

## <a name="example"></a>範例
 下列範例顯示如何在範本中使用數個自訂參數。 從具有下列自訂參數的範本建立專案或專案時，範本檔案中和的所有實例 `$color1$` `$color2$` 都會 `Red` 分別以和取代 `Blue` 。

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>另請參閱
- [ (Visual Studio 範本的 CustomParameter 元素) ](../extensibility/customparameter-element-visual-studio-templates.md)
- [範本參數](../ide/template-parameters.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
