---
title: .VSCT XML 架構條件式屬性 |Microsoft Docs
description: 瞭解如何將條件式屬性套用至 .VSCT XML 架構清單和專案。 屬性評估為 true 或 false，可控制產生的輸出。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bc1bcb9d80474b467e90de6262e797087589065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062352"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>.VSCT XML 架構條件式屬性
您可以將條件屬性套用至所有清單和專案。 邏輯運算子和符號展開運算式的評估結果為 true 或 false。 若為 true，則產生的輸出中會包含相關聯的清單或專案。

 您可以針對其他標記展開或常數測試權杖擴充。 函數 `Defined()` 會測試是否已定義特定名稱，即使沒有值也是一樣。

 當 Condition 屬性套用至清單時，此條件會套用至清單中的每個子項目。 如果子項目本身包含 Condition 屬性，則它的條件會與 AND 運算的父運算式結合。

 值1、' 1 ' 和 ' true ' 會評估為 true，而0、' 0 ' 和 ' false ' 會評估為 false。

## <a name="operators"></a>運算子
 使用下列運算子來評估條件運算式。

|運算子|定義|
|--------------|----------------|
|(,)|群組|
|!|邏輯 NOT|
|\<, >, \<=, >=, ==, !=|關係與相等|
|及|Boolean|
|或|Boolean|

## <a name="examples"></a>範例

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (。.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
