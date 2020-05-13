---
title: 吉德符號元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711120"
---
# <a name="guidsymbol-element"></a>吉德符號元素
該`GuidSymbol`元素包含表示功能表、組或命令的 GUID:ID 對的 GUID。 ID 來自元素`IDSymbol``GuidSymbol`中的元素。 元素`GuidSymbol`具有一`name`個 屬性,該屬性為 GUID 提供友好名稱,`value`該名稱包含在 屬性中。

## <a name="syntax"></a>語法

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|NAME|必要。 GUID 符號的名稱。|
|value|必要。 GUID 符號的 GUID。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含表示功能表、組或命令的 GUID:ID 對的 ID。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[符號元素](../extensibility/symbols-element.md)|對`GuidSymbol` *.vsct*檔案中的元素進行群組。|

## <a name="remarks"></a>備註
 通常 *,.vsct*檔`Symbols``GuidSymbol`部分包含三 個元素,一個用於包本身,一個用於命令集(包提供的功能表、組和命令的集合),另一個用於為按鈕和其他可視元件提供圖示的位圖。 指定元素`IDSymbol``GuidSymbol`的元素必須具有唯一的`value`。但是,`IDSymbol`具有相同值的元素可以存在於包中,只要它們具有不同的父項。

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
