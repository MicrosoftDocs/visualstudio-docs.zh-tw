---
title: " (Visual Studio 範本的 PreviewImage 元素) |Microsoft Docs"
description: 瞭解 PreviewImage 元素，以及它如何指定將出現在 [新增專案] 或 [加入新專案] 對話方塊中的預覽影像檔案名。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fc7a370885d24a586262bebd4182daacd84a9b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090222"
---
# <a name="previewimage-element-visual-studio-templates"></a> (Visual Studio 範本的 PreviewImage 元素) 
針對將出現在 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中的預覽影像，指定預覽影像（以檔案名表示）。

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Syntax

```
<PreviewImage>"filename"</PreviewImage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是代表檔案名的字串。

## <a name="remarks"></a>備註
  是選擇性元素。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
