---
title: ButtonText 元素 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739902"
---
# <a name="buttontext-element"></a>ButtonText 元素
此欄位可讓您指定出現在各種功能表中的文字。 依預設，專案 `ButtonText` 會出現在功能表控制器中。 `ButtonText`如果其他文字欄位是空白的，元素也會成為預設值。 `ButtonText`即使已指定其他文字欄位，元素也不能空白。

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

|項目|描述|
|-------------|-----------------|
|[Strings 元素](../extensibility/strings-element.md)|將文字元素分組，例如 `ButtonText` 和 `CommandName` 。|

## <a name="text-value"></a>文字值
 專案的文字值 `ButtonText` 會提供針對功能表項目、combos 和其他使用者介面所顯示的文字， (UI) 具有可見文字的元素。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
