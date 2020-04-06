---
title: 預覽圖像元素(視覺工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f20cfe5f3ef35b23a52972ef1e3b7d9d4adc5a39
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702011"
---
# <a name="previewimage-element-visual-studio-templates"></a>預覽影像元素(視覺工作室範本)
為將顯示在 **「新專案**」或 **「添加新項目**」對話框中的預覽圖像指定預覽影像(作為檔名)。

 \<VStemplate \<\<>模板数据>预览图像>

## <a name="syntax"></a>語法

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 對樣本進行分類,並定義如何在 **「新專案**」或「**新增新項目**」對話框中顯示範本。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是表示檔名的字串。

## <a name="remarks"></a>備註
  是選擇性元素。

## <a name="see-also"></a>另請參閱
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
