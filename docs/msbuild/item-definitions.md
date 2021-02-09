---
title: 項目定義 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 ItemGroup 和 ItemDefinitionGroup 來宣告專案檔中專案的中繼資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 754080defd50bc10af501fdbaf509bafe549dcbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913971"
---
# <a name="item-definitions"></a>項目定義

MSBuild 2.0 使用 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 元素，啟用專案檔中專案的靜態宣告。 不過，您只能在項目層級新增中繼資料，即使所有項目的中繼資料都相同也是如此。 從 MSBuild 3.5 開始，名為 [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) 的專案元素會克服這項限制。 *ItemDefinitionGroup* 可讓您定義一組項目定義，這些項目定義會將預設的中繼資料值，新增到具名項目類型中的所有項目。

*ItemDefinitionGroup* 元素會緊接在專案檔的 [Project](../msbuild/project-element-msbuild.md) 元素之後出現。 項目定義提供下列功能：

- 您可以為目標外的項目定義全域預設中繼資料。 亦即，相同的中繼資料會適用於指定類型的所有項目。

- 項目類型可以有多個定義。 將額外的中繼資料規格新增到類型時，最後一個規格會具有最高的優先順序。 \(中繼資料的匯入順序會比照屬性所依循的相同順序。\)

- 中繼資料可供附加。 例如，CDefines 值會根據所要設定的屬性，有條件地累加。 例如： `MT;STD_CALL;DEBUG;UNICODE` 。

- 中繼資料可被移除。

- 您可以使用條件來控制是否要包含中繼資料。

## <a name="item-metadata-default-values"></a>項目中繼資料預設值

在 ItemDefinitionGroup 中定義的項目中繼資料只是預設中繼資料的宣告。 除非您定義一個使用 ItemGroup 來包含中繼資料值的「項目」，否則不會套用中繼資料。

> [!NOTE]
> 在本主題的許多範例中都有顯示 ItemDefinitionGroup 元素，但為了清楚起見，已省略其對應的 ItemGroup 定義。

在 ItemGroup 中明確定義之中繼資料的優先順序會高於 ItemDefinitionGroup 中的中繼資料。 ItemDefinitionGroup 中的中繼資料只會套用至 ItemGroup 中未定義的中繼資料。 例如：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

在此範例中，預設中繼資料 "m" 會套用至項目 "i"，因為項目 "i" 未明確定義中繼資料 "m"。 不過，預設中繼資料 "n" 不會套用至項目 "i"，因為項目 "i" 已經定義中繼資料 "n"。

> [!NOTE]
> XML 元素和參數名稱有區分大小寫。 項目中繼資料和項目\/屬性名稱不區分大小寫。 因此，ItemDefinitionGroup 項目如果名稱只有大小寫不同，應該視為相同的 ItemGroup。

## <a name="value-sources"></a>值來源

ItemDefinitionGroup 中所定義之中繼資料的值可以來自許多不同的來源，如下所示：

- PropertyGroup 屬性

- 來自 ItemDefinitionGroup 的項目

- ItemDefinitionGroup 項目上的項目轉換

- 環境變數

- 從 *MSBuild.exe* 命令列 (的全域屬性) 

- 保留的屬性

- 來自 ItemDefinitionGroup 之項目上的常見中繼資料

- CDATA 區段 \<\!\[CDATA\[anything here is not parsed\]\]\>

> [!NOTE]
> 來自 ItemGroup 的項目中繼資料在 ItemDefinitionGroup 中繼資料宣告中沒有用處，因為系統會先處理 ItemDefinitionGroup 元素，然後才處理 ItemGroup 元素。

## <a name="additive-and-multiple-definitions"></a>新增及多個定義

當您新增定義或使用多個 ItemDefinitionGroups 時，請記住下列事項：

- 額外的中繼資料規格會新增到類型。

- 最後一個規格會具有最高的優先順序。

當您具有多個 ItemDefinitionGroups 時，每個後續的規格都會將其中繼資料新增到先前的定義。 例如：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

在此範例中，中繼資料 "o" 會新增到 "m" 和 "n"。

此外，也可以新增先前定義的中繼資料值。 例如：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

在此範例中，中繼資料 "m" 的先前定義值 \(m1\) 會新增到新的值 \(m2\)，因此最終的值會是 "m1;m2"。

> [!NOTE]
> 這也可能發生在相同的 ItemDefinitionGroup 中。

當您覆寫先前定義的中繼資料時，最後一個規格會具有最高的優先順序。 在下列範例中，中繼資料 "m" 的最終值會從 "m1" 變成 "m1a"。

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>在 ItemDefinitionGroup 中使用條件

您可以在 ItemDefinitionGroup 中使用條件來控制是否要包含中繼資料。 例如：

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

在此案例中，只有當 "Configuration" 屬性的值為 "Debug" 時，才會包含項目 "i" 上的預設中繼資料 "m1"。

> [!NOTE]
> 條件中僅支援本機中繼資料參考。

對先前 ItemDefinitionGroup 中所定義之中繼資料的參考是項目 (而非定義群組) 的本機中繼資料參考。 亦即，參考的範圍為項目專用。 例如：

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

在上述範例中，項目 "i" 在其 Condition 中參考了項目 "test"。 這個 Condition 永遠不會成立，因為 MSBuild 會將對 ItemDefinitionGroup 中另一個項目中繼資料的參考解譯為空字串。 因此，"m" 會設定為 "m0"。

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

在上述範例中，"m" 會設定為 "m1" 值，因為 Condition 針對項目 "yes" 參考了項目 "i" 的中繼資料值。

## <a name="override-and-delete-metadata"></a>覆寫及刪除中繼資料

在 ItemDefinitionGroup 元素中定義的中繼資料，可以藉由將中繼資料值設定為另一個值，在後續的 ItemDefinitionGroup 元素中覆寫。 您也可以藉由將中繼資料項目設定為空值，來有效地刪除中繼資料項目。 例如：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

項目 "i" 仍然包含中繼資料 "m"，但其值現在是空的。

## <a name="scope-of-metadata"></a>中繼資料的範圍

在已定義及全域的屬性上，只要定義了 ItemDefinitionGroups，ItemDefinitionGroups 就具有全域範圍。 ItemDefinitionGroup 中的預設中繼資料定義可以自我參考。 例如，以下使用一個簡單的中繼資料參考：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

也可以使用限定的中繼資料參考：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

不過，以下無效：

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

從 MSBuild 3.5 開始，ItemGroups 也可以是自我參考。 例如：

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>另請參閱

- [批次處理](../msbuild/msbuild-batching.md)
