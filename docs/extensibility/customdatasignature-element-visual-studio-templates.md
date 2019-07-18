---
title: CustomDataSignature 元素 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db2b4d089495245d1a37469df1dc43a19be31866
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351969"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>CustomDataSignature 元素 （Visual Studio 範本）
指定的文字簽章，以尋找自訂資料。

 \<VSTemplate > \<TemplateData > \<CustomDataSignature >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，以及定義如何顯示在**新的專案**或**加入新項目** 對話方塊。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字會是具有文字簽章，才能找出的自訂資料的字串。

## <a name="remarks"></a>備註
 `CustomDataSignature` 是選擇性項目。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)