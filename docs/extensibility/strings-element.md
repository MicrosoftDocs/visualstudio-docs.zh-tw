---
title: 字串元素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719436"
---
# <a name="strings-element"></a>Strings 項目
字串元素必須至少包含一個**ButtonText**的子項目。 所有其他子專案都是選擇性的。 不正確 XML 字元，例如 ' & ' 和 ' < ' 必須編碼為實體（' &amp; ' 和 ' &lt; ' 等等）。

 文字字串中的連字號會指定命令的鍵盤快速鍵。

## <a name="syntax"></a>語法

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|語言|選擇項。 Language = "."。|

### <a name="child-elements"></a>子項目

|項目|描述|
|-------------|-----------------|
|ButtonText|此欄位和命令定義中的五個下列文字欄位，可讓您指定出現在各種功能表中的文字。 根據預設，[`ButtonText`] 欄位會顯示在功能表控制器中。 如果其他文字欄位為空白，[`ButtonText`] 欄位也會變成預設值。 即使指定其他文字欄位，`ButtonText` 欄位也不能空白。|
|ToolTipText|[@No__t_0] 欄位會指定功能表項目的工具提示中所顯示的文字。<br /><br /> 如果 [`ToolTipText`] 欄位為空白，則會使用 [`ButtonText`] 欄位。|
|MenuText|[@No__t_0] 欄位會指定當命令位於主功能表、工具列、快捷方式功能表或子功能表中時，所顯示的文字。 如果 [`MenuText`] 欄位是空白的，整合式開發環境（IDE）會使用 [`ButtonText`] 欄位。 [@No__t_0] 欄位也可以用於當地語系化。<br /><br /> 對於快捷方式功能表，[`MenuText`] 欄位是顯示在快捷方式功能表工具列中的名稱，可讓您自訂 IDE 中的快捷方式功能表。 因此，請在您為快捷方式功能表命名的情況下明確指定。例如，使用 [Widget 套件快捷方式功能表]，而不是 [快捷方式]。<br /><br /> 如果未指定 [`MenuText`] 欄位，則會使用 [`ButtonText`] 欄位。|
|CommandName|[@No__t_0] 欄位會在 [**自訂**] 對話方塊的 [**命令**] 索引標籤中，指定出現在鍵盤類別目錄中的文字（按一下 [**工具**] 功能表上的 [**自訂**] 即可取得）。|
|CanonicalName|[英文 `CanonicalName`] 欄位會以英文文字指定可在 [**命令**] 視窗中輸入以執行功能表項目的命令名稱。 IDE 會去除不是字母、數位、底線或內嵌句點的任何字元。 然後，這段文字會串連到 `ButtonText` 欄位，以定義命令。 例如，[檔案 **] 功能表上的 [** **新增專案**] 會變成 [NewProject] 命令。<br /><br /> 如果未指定 [英文 `CanonicalName`] 欄位，IDE 就會使用 [`ButtonText`] 欄位，並去除字母、數位、底線和內嵌句點以外的所有字元。 例如，按鈕文字「& 定義命令 ...」會變成 DefineCommands，其中的連字號、空格和省略號會被移除。<br /><br /> 如果指定了 `TextChanges` 旗標，且已變更命令的文字，則**命令**視窗所辨識的對應命令不會變更;它仍然是原始 `ButtonText` 或英文 `CanonicalName` 欄位的標準格式。|
|LocCanonicalName|[@No__t_0] 欄位的行為與 [英文 `CanonicalName`] 欄位相同，但可指定當地語系化的命令文字。 可以同時指定這兩個標準欄位。 因為 IDE 只會剖析在**命令**視窗中輸入的文字，並將它與命令建立關聯，所以英文和非英文文字都可以與相同的命令相關聯。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[Button 元素](../extensibility/button-element.md)|定義使用者可以與之互動的元素。|
|[Menu 元素](../extensibility/menu-element.md)|定義單一功能表項目。|
|[Combo 元素](../extensibility/combo-element.md)|定義出現在下拉式方塊中的命令。|

## <a name="see-also"></a>請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)