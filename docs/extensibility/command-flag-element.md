---
title: 命令旗標項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a38708d6256556693b7ab1dfc8c04b79f484ee8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334844"
---
# <a name="command-flag-eelement"></a>命令旗標 Eelement
修改其父項目。

## <a name="syntax"></a>語法

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下一節會描述有效的項目值。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|值|描述|
|-----------|-----------------|
|AllowParams|表示使用者可以輸入中的命令參數**命令**視窗中輸入命令的正式名稱時。<br /><br /> 適用於： `Button`|
|AlwaysCreate|功能表會建立，即使它有任何群組或按鈕。<br /><br /> 適用於： `Menu`|
|CaseSensitive|使用者項目會區分大小寫。<br /><br /> 適用於： `Combo`|
|CommandWellOnly|如果命令未出現在最上層功能表上，而且您想要適用於其他的 shell 自訂項目，例如，適用於繫結至鍵盤快速鍵，請套用這個旗標。 VSPackage 安裝之後，您還可以自訂這些命令，開啟**選項**] 對話方塊中，然後編輯 [命令位置底下**鍵盤環境**類別目錄。 這個旗標不會影響快顯功能表、 工具列、 功能表控制站或子功能表上的位置。<br /><br /> 適用於： `Button`， `Combo`|
|DefaultDisabled|根據預設，已停用命令如果未載入 VSPackage 實作它或`QueryStatus`尚未呼叫方法。<br /><br /> 適用於： `Button`， `Combo`|
|DefaultDocked|依預設停駐。 此設定不會再套用至工具列，因為一律停駐。|
|DefaultInvisible|根據預設，命令不會察覺，如果未載入 VSPackage 實作它或`QueryStatus`尚未呼叫方法。<br /><br /> 我們建議您合併這與`DynamicVisibility`旗標。<br /><br /> 適用於： `Button`， `Combo`， `Menu`|
|DontCache|在開發環境並不會快取`QueryStatus`方法的結果，此命令。<br /><br /> 為功能表中，這會告訴功能表控制器不是用來快取其功能表項目的文字。 當功能表包含動態項目或動態文字的項目時，請使用這個旗標。<br /><br /> 適用於： `Button`， `Menu`|
|DynamicItemStart|表示動態清單的開頭。 這可讓環境，以建立清單，藉由後續呼叫`QueryStatus`直到傳回 OLECMDERR_E_UNSUPPORTED 旗標的清單項目上的方法。 這適用於項目，例如最近使用的 (MRU) 清單及視窗清單。<br /><br /> 適用於： `Button`|
|DynamicVisibility|此命令的可見性可以透過變更`QueryStatus`方法或透過在內容中包含的 GUID`VisibilityConstraints`一節。<br /><br /> 適用於顯示功能表和工具視窗工具列中，而不是會出現在主視窗的最上層工具列上的命令。 最上層工具列項目可以停用，但並未隱藏，請從傳回 OLECMDF_INVISIBLE 旗標時`QueryStatus`方法。 出現在工作視窗工具列的工具列命令可以隱藏。<br /><br /> 在功能表上，這個旗標也會指出，它應該會自動隱藏其所有成員都隱藏時。 這個旗標通常會指派給子功能表，因為已經有最上層功能表的這個行為。<br /><br /> 這個旗標應該要結合`DefaultInvisible`旗標。<br /><br /> 適用於： `Button`， `Combo`， `Menu`|
|FilterKeys|請參閱底下的篩選索引鍵主題[Combo 元素](../extensibility/combo-element.md)。<br /><br /> 適用於： `Combo`|
|FixMenuController|如果此命令位於功能表控制器，此命令永遠是預設值;亦即，每當在選取功能表控制器按鈕本身，是所選取的命令。 功能表控制器是否`TextIsAnchorCommand`加上旗標集，則功能表控制器也會在它的文字的命令，從`FixMenuController`旗標。<br /><br /> 只有一個命令，功能表控制器上的應該有`FixMenuController`旗標。 如果如此標示一個以上的命令，在功能表中的最後一個命令會變成預設命令。<br /><br /> 適用於： `Button`|
|IconAndText|在功能表和工具列上顯示的圖示和文字。<br /><br /> 適用於： `Button`， `Combo`， `Menu`|
|NoAutoComplete|已停用自動完成功能。<br /><br /> 適用於： `Combo`|
|NoButtonCustomize|請勿讓使用者可以自訂此按鈕。<br /><br /> 適用於： `Button`， `Combo`|
|NoKeyCustomize|請勿啟用鍵盤自訂。<br /><br /> 適用於： `Button`， `Combo`|
|NoShowOnMenuController|如果此命令位於功能表控制器，命令就不會出現在下拉式清單中。<br /><br /> 適用於： `Button`|
|NotInTBList|不會顯示在 可用工具列的清單。 這是只適用於工具列功能表類型。<br /><br /> 適用於： `Menu`|
|NoToolbarClose|使用者無法關閉工具列。 這是只適用於工具列功能表類型。<br /><br /> 適用於： `Menu`|
|pict|只上顯示圖示的工具列上，但只有在功能表上的文字。 如果指定了無圖示，顯示可點按的空白區域工具列上。<br /><br /> 適用於： `Button`|
|PostExec|可讓命令未封鎖。 在開發環境會延後執行，直到完成所有的前置處理查詢。<br /><br /> 適用於： `Button`|
|RouteToDocs|此命令會路由至使用中文件。<br /><br /> 適用於： `Button`|
|StretchHorizontally|當設定這個旗標時，寬度會變成下拉式方塊的最小寬度，如果沒有在工具列上的空間，下拉式方塊會自動縮放以填滿可用空間。 會發生這種情況是只有水平停駐工具列，而且在工具列上的一個下拉式方塊可以使用旗標 （在第一個下拉式方塊以外的所有項，則會忽略此旗標）。<br /><br /> 適用於： `Combo`|
|TextMenuUseButton|使用`ButtonText`功能表的欄位。 預設欄位是`MenuText`如果有指定。<br /><br /> 適用於： `Button`|
|TextChanges|命令或功能表變更的文字可以在執行階段，通常透過`QueryStatus`方法。<br /><br /> 適用於： `Button`， `Menu`|
|TextChangesButton|適用於： `Button`|
|TextIsAnchorCommand|功能表控制站的功能表文字是來自預設 （錨點） 命令。 錨定命令是選取或閂鎖的最後一個命令。 如果未設定此旗標，功能表控制器會使用它自己`MenuText`欄位。 不過，按一下功能表控制器仍會啟用選取的最後一個命令，從該控制站。<br /><br /> 我們建議您將結合使用這個旗標`TextChanges`旗標。<br /><br /> 這個旗標僅適用於類型的功能表 MenuController 或 MenuControllerLatched。<br /><br /> 適用於： `Menu`|
|TextMenuCtrlUseMenu|使用`MenuText`功能表控制站上的欄位。 預設欄位是`ButtonText`。<br /><br /> 適用於： `Button`|
|TextMenuUseButton|使用`ButtonText`功能表的欄位。 預設欄位是`MenuText`如果有指定。<br /><br /> 適用於： `Button`|
|TextOnly|只會顯示文字的工具列或功能表但無圖示即使未指定圖示。<br /><br /> 適用於： `Button`|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[Buttons 元素](../extensibility/buttons-element.md)|提供的群組[Button 元素](../extensibility/button-element.md)項目。|
|[功能表項目](../extensibility/menus-element.md)|定義實作 VSPackage 的所有功能表。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)