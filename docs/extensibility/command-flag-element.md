---
title: 命令旗標元素 |Microsoft Docs
description: 命令旗標元素會修改其父元素。 檢查其父元素和子項目。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f9f9db3d7a8146bd7b44cf779fd62fd75803d86
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089637"
---
# <a name="command-flag-eelement"></a>命令旗標 Eelement
修改其父元素。

## <a name="syntax"></a>Syntax

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下一節將描述有效的元素值。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|值|描述|
|-----------|-----------------|
|AllowParams|指出當使用者輸入命令的正式名稱時，可以在 **命令** 視窗中輸入命令參數。<br /><br /> 有效期限： `Button`|
|AlwaysCreate|即使沒有群組或按鈕，也會建立功能表。<br /><br /> 有效期限： `Menu`|
|CaseSensitive|使用者專案會區分大小寫。<br /><br /> 有效期限： `Combo`|
|CommandWellOnly|如果命令未出現在最上層功能表，而您想要讓它可供其他 shell 自訂使用（例如，將它系結至鍵盤快速鍵），請套用此旗標。 安裝 VSPackage 之後，您可以開啟 [ **選項** ] 對話方塊，然後在 [ **鍵盤環境** ] 類別下編輯命令位置，以自訂這些命令。 此旗標不會影響快捷方式功能表、工具列、功能表控制器或子功能表上的位置。<br /><br /> 適用于： `Button` 、 `Combo`|
|DefaultDisabled|根據預設，如果未載入執行它的 VSPackage，或尚未呼叫方法，則會停用此命令 `QueryStatus` 。<br /><br /> 適用于： `Button` 、 `Combo`|
|DefaultDocked|預設為固定。 此設定不會再套用至工具列，因為它們一律停駐。|
|DefaultInvisible|根據預設，如果未載入執行它的 VSPackage，或尚未呼叫方法，則不會看到此命令 `QueryStatus` 。<br /><br /> 建議您結合此旗標與 `DynamicVisibility` 旗標。<br /><br /> 適用于： `Button` 、 `Combo` 、 `Menu`|
|DontCache|開發環境不會快取 `QueryStatus` 此命令的方法結果。<br /><br /> 針對功能表，這會告知功能表控制器不要快取其功能表項目的文字。 當功能表包含動態專案或有動態文字的專案時，請使用此旗標。<br /><br /> 適用于： `Button` 、 `Menu`|
|DynamicItemStart|表示動態清單的開頭。 如此一來，環境就可以藉由連續呼叫 `QueryStatus` 清單專案上的方法來建立清單，直到傳回 OLECMDERR_E_UNSUPPORTED 旗標為止。 這非常適用于最近使用 (MRU) 清單和視窗清單等專案。<br /><br /> 有效期限： `Button`|
|DynamicVisibility|您可以透過 `QueryStatus` 方法或透過包含在區段中的內容 GUID 來變更命令的可見度 `VisibilityConstraints` 。<br /><br /> 適用于出現在功能表和工具視窗工具列上的命令，而不是出現在主視窗的最上層工具列上。 當從方法傳回 OLECMDF_INVISIBLE 旗標時，可以停用但無法隱藏最上層工具列專案 `QueryStatus` 。 可以隱藏工具視窗工具列上顯示的工具列命令。<br /><br /> 在功能表上，此旗標也會指出它應該在隱藏所有成員時自動隱藏。 此旗標通常會指派給子功能表，因為最上層功能表已經有此行為。<br /><br /> 此旗標應與旗標合併 `DefaultInvisible` 。<br /><br /> 適用于： `Button` 、 `Combo` 、 `Menu`|
|L|請參閱 [組合式元素](../extensibility/combo-element.md)底下的篩選按鍵主題。<br /><br /> 有效期限： `Combo`|
|FixMenuController|如果此命令位於功能表控制器上，則此命令一律為預設值。也就是說，只要選取功能表控制器按鈕本身，就會選取此命令。 如果功能表控制器已 `TextIsAnchorCommand` 設定旗標，則功能表控制器也會從具有旗標的命令取得其文字 `FixMenuController` 。<br /><br /> 功能表控制器上只有一個命令應該有旗標 `FixMenuController` 。 如果有一個以上標示的命令，功能表中的最後一個命令會變成預設命令。<br /><br /> 有效期限： `Button`|
|IconAndText|在功能表和工具列上顯示圖示和文字。<br /><br /> 適用于： `Button` 、 `Combo` 、 `Menu`|
|NoAutoComplete|自動完成功能已停用。<br /><br /> 有效期限： `Combo`|
|NoButtonCustomize|請勿讓使用者自訂此按鈕。<br /><br /> 適用于： `Button` 、 `Combo`|
|NoKeyCustomize|請勿啟用鍵盤自訂。<br /><br /> 適用于： `Button` 、 `Combo`|
|NoShowOnMenuController|如果這個命令位於功能表控制器上，則命令不會出現在下拉式清單中。<br /><br /> 有效期限： `Button`|
|NotInTBList|不會出現在可用的工具列清單中。 這只對工具列功能表類型有效。<br /><br /> 有效期限： `Menu`|
|NoToolbarClose|使用者無法關閉工具列。 這只對工具列功能表類型有效。<br /><br /> 有效期限： `Menu`|
|Pict|只顯示工具列上的圖示，但是只顯示功能表上的文字。 如果未指定圖示，則會在工具列上顯示可按一下的空白空間。<br /><br /> 有效期限： `Button`|
|PostExec|使命令成為未封鎖。 開發環境會順延強制，直到所有前置處理查詢都完成為止。<br /><br /> 有效期限： `Button`|
|RouteToDocs|此命令會路由傳送至使用中的檔。<br /><br /> 有效期限： `Button`|
|StretchHorizontally|當設定這個旗標時，寬度會變成下拉式方塊的最小寬度，如果工具列上有空間，下拉式方塊就會伸展以填滿可用的空間。 只有當工具列水準停駐時，工具列上只有一個下拉式方塊可以使用旗標 (旗標會在第一個下拉式方塊) 以外的所有情況下，略過旗標。<br /><br /> 有效期限： `Combo`|
|TextChanges|您可以在執行時間變更命令或功能表文字，通常是透過方法來變更 `QueryStatus` 。<br /><br /> 適用于： `Button` 、 `Menu`|
|TextChangesButton|有效期限： `Button`|
|TextIsAnchorCommand|若為功能表控制器，則會從預設的 (錨點) 命令取得功能表文字。 錨點命令是最後選取或鎖定的命令。 如果未設定此旗標，則功能表控制器會使用它自己的 `MenuText` 欄位。 但是，按一下功能表控制器仍會啟用該控制器的最後一個選取的命令。<br /><br /> 我們建議您將此旗標與旗標合併 `TextChanges` 。<br /><br /> 此旗標只適用于 MenuController 或 MenuControllerLatched 類型的功能表。<br /><br /> 有效期限： `Menu`|
|TextMenuCtrlUseMenu|使用 `MenuText` 功能表控制器上的欄位。 預設欄位為 `ButtonText` 。<br /><br /> 有效期限： `Button`|
|TextMenuUseButton|使用 `ButtonText` 功能表的欄位。 如果已指定，則預設欄位為 `MenuText` 。<br /><br /> 有效期限： `Button`|
|TextOnly|即使已指定圖示，也只會在工具列或功能表上顯示文字，但不顯示圖示。<br /><br /> 有效期限： `Button`|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[按鈕元素](../extensibility/buttons-element.md)|提供 [按鈕元素](../extensibility/button-element.md) 元素的群組。|
|[Menu 元素](../extensibility/menus-element.md)|定義 VSPackage 所實行的所有功能表。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (。.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
