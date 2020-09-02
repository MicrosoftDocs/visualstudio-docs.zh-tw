---
title: " (Visual Studio 範本的 CustomParameter 元素) |Microsoft Docs"
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739424"
---
# <a name="customparameter-element-visual-studio-templates"></a> (Visual Studio 範本的 CustomParameter 元素) 
包含從範本建立專案或專案時所要使用的自訂參數名稱和值。

## <a name="syntax"></a>語法

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Name`|必要。 參數名稱。 參數的格式為 $*name*$。|
|`Value`|必要。 參數的取代值。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|當 wizard 進行參數取代時，將要傳遞給範本嚮導的自訂參數分組。|

## <a name="remarks"></a>備註
 當範本包含 `CustomParameter` 專案時，每個實例 `Name` 都會將屬性取代為 `Value` 所建立專案或專案檔中的屬性。

## <a name="example"></a>範例
 下列範例顯示如何在範本中使用數個自訂參數。 從具有下列自訂參數的範本建立專案或專案時，範本檔案中和的所有實例 `$color1$` `$color2$` 都會 `Red` 分別以和取代 `Blue` 。

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>另請參閱
- [ (Visual Studio 範本的 CustomParameters 元素) ](../extensibility/customparameters-element-visual-studio-templates.md)
- [範本參數](../ide/template-parameters.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
