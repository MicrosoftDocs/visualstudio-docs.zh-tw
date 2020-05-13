---
title: 按鍵文字元素 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739902"
---
# <a name="buttontext-element"></a>按鈕文字元素
此欄位允許您指定出現在各種選單中的文字。 預設情況下,該`ButtonText`元素將顯示在菜單控制器中。 如果`ButtonText`其他文字欄位為空,則元素也變為預設值。 即使`ButtonText`指定了其他文本欄位,元素也不能為空。

## <a name="syntax"></a>語法

```xml
<ButtonText>My Command</ButtonText>
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
|[字串元素](../extensibility/strings-element.md)|文字元素(如`ButtonText`與`CommandName`)|

## <a name="text-value"></a>文字值
 `ButtonText`元素的文本值提供為功能表項、組合和其他具有可見文本的使用者介面 (UI) 元素顯示的文本。

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
