---
title: " (Visual Studio 範本的 CustomDataSignature 元素) |Microsoft Docs"
description: 深入瞭解 CustomDataSignature 元素，以及它如何指定文字簽章以找出自訂資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0b2442e7b254ccaaf9e890b5370f712b5715f18
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671515"
---
# <a name="customdatasignature-element-visual-studio-templates"></a> (Visual Studio 範本的 CustomDataSignature 元素) 
指定要尋找自訂資料的文字簽章。

 \<VSTemplate> \<TemplateData>
 \<CustomDataSignature>

## <a name="syntax"></a>語法

```
<CustomDataSignature>"string"</CustomDataSignature>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字是具有尋找自訂資料所需之文字簽章的字串。

## <a name="remarks"></a>備註
  是選擇性元素。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
