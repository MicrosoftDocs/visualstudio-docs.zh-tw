---
title: 自定義數據簽名元素(可視化工作室範本) |微軟文件
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
ms.openlocfilehash: ec8bae34da0f007bac65f26c4e442c1d03e56d08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739437"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>自訂資料簽名元素(視覺化工作室範本)
指定文字簽章以尋找自訂資料。

 \<樣本>\<樣本資料>\<自訂資料簽名>

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

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 對樣本進行分類,並定義如何在 **「新專案**」或「**新增新項目**」對話框中顯示範本。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字是具有尋找自訂資料所需的文字簽名的字串。

## <a name="remarks"></a>備註
  是選擇性元素。

## <a name="see-also"></a>另請參閱
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
