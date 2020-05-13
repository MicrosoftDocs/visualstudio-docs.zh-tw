---
title: 裝配元件(可視化工作室範本) |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740041"
---
# <a name="assembly-element-visual-studio-templates"></a>裝配元件(可視化工作室範本)
指定有關程式集的資訊,範本用於將該程式集的引用添加到專案。

 \<樣本>\<範本內容>\<參考>\<參考>\<程式集>

## <a name="syntax"></a>語法

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

 此文字指定在實例化專案樣本時要添加到專案的程式集。 必須透過以下方式的一個指定此程式集名稱:

- 作為完整的程式集名稱。 例如：

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- 作為簡單的文本引用。 例如：

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>備註
 `Assembly` 是 `Reference` 的必要子項目。

 `References,``Reference`和`Assembly`元素只能在具有`Type`屬性值`Item`的 *.vstemplate*檔案中使用。

## <a name="example"></a>範例
 下面的示例說明了項範本`TemplateContent`的元素。 此 XML 添加對*System.dll*和*System.Data.dll*程式集的引用。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
