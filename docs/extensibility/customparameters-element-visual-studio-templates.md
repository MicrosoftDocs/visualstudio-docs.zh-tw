---
title: 自定義參數元素(可視化工作室範本) |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739417"
---
# <a name="customparameters-element-visual-studio-templates"></a>自訂參數元素(視覺化工作室範本)
對嚮導進行參數替換時要傳遞給範本嚮導的自定義參數進行分組。

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

|元素|描述|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 包含自定義參數名稱和值,用於從範本創建專案或項時使用。 `CustomParameter` 元素中可能有零個或多個 `CustomParameters` 元素。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|

## <a name="remarks"></a>備註

## <a name="example"></a>範例
 下面的範例展示如何在範本中使用多個自定義參數。 從您有以下自訂參數的樣本建立項目或項目`$color1$`, 樣本檔中的所有實體會`$color2$`取代為`Red`與`Blue`。

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>另請參閱
- [自訂參數元素(視覺化工作室範本)](../extensibility/customparameter-element-visual-studio-templates.md)
- [範本參數](../ide/template-parameters.md)
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
