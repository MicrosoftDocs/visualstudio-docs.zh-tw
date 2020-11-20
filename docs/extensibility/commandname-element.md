---
title: CommandName 元素 |Microsoft Docs
description: CommandName 專案會在 [選項] 對話方塊和 [自訂] 對話方塊的命令清單中，指定出現在鍵盤類別中的文字。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandName element (VSCT XML schema)
- VSCT XML schema elements, CommandName
ms.assetid: a338b767-aa7e-4536-9908-e19a50ab60ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8447213b14a3632197ea7ce27677423460315f71
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974115"
---
# <a name="commandname-element"></a>CommandName 元素
專案 `CommandName` 會在 [選項] 對話方塊的 [**選項**] 對話方塊中，以及在 [**自訂**] 對話方塊的 **命令** 清單中，指定出現在鍵盤類別中的文字。

## <a name="syntax"></a>語法

```
<CommandName>MyCommand</CommandName>
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

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
