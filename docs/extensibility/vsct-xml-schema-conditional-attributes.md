---
title: VSCT XML 架構條件屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697939"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 架構條件屬性
您可以將條件屬性應用於所有清單和項。 邏輯運算符和符號擴展運算式計算為真或假。 如果為 true,則關聯的清單或項包含在生成的輸出中。

 您可以針對其他權碼延伸或常量測試權杖擴展。 函數`Defined()`測試是否定義了特定名稱,即使它沒有值。

 當條件屬性應用於清單時,條件將應用於清單中的每個子元素。 如果子元素本身包含條件屬性,則其條件將通過 AND 操作與父表達式組合。

 值 1、"1"和"true"被計算為 true,0、"0"和"false"被計算為 false。

## <a name="operators"></a>操作員
 使用以下運算符計算條件表達式。

|運算子|定義|
|--------------|----------------|
|(,)|分組|
|!|邏輯 NOT|
|\<, >, \<*, >= , * , !|關係與相等|
|和|Boolean|
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
- [視覺化工作室命令表 (.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
