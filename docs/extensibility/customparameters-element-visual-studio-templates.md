---
title: CustomParameters 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61b8c3812f90d435da8aaa1e6e3d7a4f4a61e807
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705985"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters 項目 （Visual Studio 範本）
群組精靈會讓參數替代項目時，要傳遞至 [範本] 精靈的自訂參數。

## <a name="syntax"></a>語法

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

|項目|描述|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 包含自訂的參數名稱和值，以從範本建立專案或項目時使用。 `CustomParameter` 項目中可能有零個或多個 `CustomParameters` 項目。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|

## <a name="remarks"></a>備註

## <a name="example"></a>範例
 下列範例示範如何使用在範本中的數個自訂參數。 當從具有下列自訂參數的所有執行個體的範本建立專案或項目`$color1$`並`$color2$`範本中的檔案將會取代`Red`和`Blue`分別。

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>另請參閱
- [CustomParameter 元素 （Visual Studio 範本）](../extensibility/customparameter-element-visual-studio-templates.md)
- [範本參數](../ide/template-parameters.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)