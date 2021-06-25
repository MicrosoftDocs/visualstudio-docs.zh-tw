---
title: GuidSymbol 元素 |Microsoft Docs
description: GuidSymbol 元素包含 GUID： ID 組的 GUID，代表功能表、群組或命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c30c7a48b03b5deed3267e106e926d3cb5114c1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902757"
---
# <a name="guidsymbol-element"></a>GuidSymbol 元素
`GuidSymbol`元素包含 guid： ID 組的 guid，代表功能表、群組或命令。 識別碼來自 `IDSymbol` 元素中的元素 `GuidSymbol` 。 專案 `GuidSymbol` 具有屬性， `name` 該屬性會提供 GUID 的易記名稱，該名稱包含在屬性中 `value` 。

## <a name="syntax"></a>Syntax

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
|[IDSymbol 元素](../extensibility/idsymbol-element.md)|包含代表功能表、群組或命令之 GUID： ID 組的識別碼。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[符號元素](../extensibility/symbols-element.md)|`GuidSymbol`將 *.vsct* 檔案中的元素群組在一起。|

## <a name="remarks"></a>備註
 一般而言， *.vsct* 檔案 `GuidSymbol` 會在其區段中包含三個元素 `Symbols` ，一個用於封裝本身，一個用於命令集 (封裝提供的功能表、群組和命令的集合) ，另一個則用於提供按鈕和其他視覺效果元件圖示的點陣圖。 `IDSymbol`指定專案中的每個元素都 `GuidSymbol` 必須有唯一的 `value` 。不過， `IDSymbol` 具有相同值的專案可以存在於封裝中，前提是它們有不同的父系。

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
