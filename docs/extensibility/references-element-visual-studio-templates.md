---
title: 參考元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701607"
---
# <a name="references-element-visual-studio-templates"></a>參考元素(視覺化工作室範本)
對範本加入專案中的程式集引用進行分組。

 \<VStemplate \<\<>模板内容>引用>

## <a name="syntax"></a>語法

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[參考](../extensibility/reference-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定項目加入專案時要加入的組件參考。 元素中必須存在一`Reference``References`個或多個元素。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定範本的內容。|

## <a name="remarks"></a>備註
 `References` 是 `TemplateContent` 的選擇性子項目。

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
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
