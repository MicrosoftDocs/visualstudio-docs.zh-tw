---
title: 參考元素(視覺工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701619"
---
# <a name="reference-element-visual-studio-templates"></a>參考元素(視覺化工作室範本)
指定項目加入專案時要加入的組件參考。

 \<VStemplate \<\<>模板内容\<>参考>参考>

## <a name="syntax"></a>語法

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
|[裝配](../extensibility/assembly-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定有關程式集的資訊,範本用於將該程式集的引用添加到專案。 每個`Reference`元素中必須`Assembly`有一個元素。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[參考](../extensibility/references-element-visual-studio-templates.md)|對範本加入專案中的程式集引用進行分組。|

## <a name="remarks"></a>備註
 `Reference` 是 `References` 的必要子項目。

 `Reference`和`References`元素只能在具有`Type`屬性值`Item`的 *.vstemplate*檔案中使用。

## <a name="example"></a>範例
 下面的示例說明了項範本`TemplateContent`的元素。 此 XML 添加對*System.dll*和*System.Data.dll*程式集的引用。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
