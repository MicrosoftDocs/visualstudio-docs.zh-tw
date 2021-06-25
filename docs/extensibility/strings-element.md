---
title: Strings 元素 |Microsoft Docs
description: Strings 元素包含 ButtonText 子專案和其他選擇性子項目。 文字字串中的 & 符號會指定鍵盤快速鍵。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899403"
---
# <a name="strings-element"></a>Strings 項目
Strings 元素至少必須包含 **ButtonText** 子項目。 所有其他子項目都是選擇性的。 不正確 XML 字元，例如 ' & ' 和 ' < ' 必須編碼為實體 ( ' &amp; ' 和 ' &lt; ' 等等，) 。

 文字字串中的 & 符號會指定命令的鍵盤快速鍵。

## <a name="syntax"></a>Syntax

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|語言|選擇性。 Language = "."。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|ButtonText|在命令定義中，此欄位和五個下列文字欄位可讓您指定出現在各種功能表中的文字。 依預設， `ButtonText` 欄位會出現在功能表控制器中。 `ButtonText`如果其他文字欄位是空白的，此欄位也會成為預設值。 `ButtonText`即使已指定其他文字欄位，此欄位也不能空白。|
|ToolTipText|`ToolTipText`欄位會指定在功能表項目的工具提示中顯示的文字。<br /><br /> 如果 `ToolTipText` 欄位是空白的，則 `ButtonText` 會使用此欄位。|
|MenuText|`MenuText`欄位會指定針對命令所顯示的文字（如果它位於主功能表、工具列、快捷方式功能表或子功能表中）。 如果 `MenuText` 欄位是空白的，則 (IDE) 的整合式開發環境會使用該 `ButtonText` 欄位。 此 `MenuText` 欄位也可用於當地語系化。<br /><br /> 在快捷方式功能表中， `MenuText` 欄位是顯示在快捷方式功能表工具列中的名稱，可讓您自訂 IDE 中的快捷方式功能表。 因此，請特別針對您為快捷方式功能表命名的內容，例如，使用「Widget 封裝快捷方式功能表」，而不是「快捷方式」。<br /><br /> 如果 `MenuText` 未指定欄位，則 `ButtonText` 會使用此欄位。|
|CommandName|`CommandName`欄位會在 [**自訂**] 對話方塊的 [命令] 索引標籤中，按一下 [命令] 索引標籤中所顯示的 [**命令**] 索引標籤， (可以按一下 [**工具**] 功能表) |
|CanonicalName|[英文 `CanonicalName` ] 欄位以英文文字指定命令的名稱，您可以在 **命令** 視窗中輸入該命令以執行功能表項目。 IDE 會去除非字母、數位、底線或內嵌句號的任何字元。 然後，此文字會串連至 `ButtonText` 欄位來定義命令。 例如，[檔案 **] 功能表上的 [** **新增專案**] 會變成 NewProject 命令。<br /><br /> 如果 `CanonicalName` 未指定英文欄位，IDE 會使用該 `ButtonText` 欄位，並去除所有字母、數位、底線和內嵌句點以外的字元。 例如，按鈕文字「&定義命令 ...」變成 DefineCommands，其中的連字號、空格和省略號都會被移除。<br /><br /> 如果 `TextChanges` 指定旗標並變更命令的文字， **命令** 視窗所辨識的對應命令不會變更，而是原始 `ButtonText` 或英文欄位的標準格式 `CanonicalName` 。|
|LocCanonicalName|此 `LocCanonicalName` 欄位的行為與英文欄位相同， `CanonicalName` 但可指定當地語系化的命令文字。 您可以同時指定這兩個標準欄位。 由於 IDE 只會剖析在 **命令** 視窗中輸入的文字，並將其與命令建立關聯，因此英文和非英文文字都可以與相同的命令相關聯。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[Button 元素](../extensibility/button-element.md)|定義使用者可以與之互動的元素。|
|[Menu 元素](../extensibility/menu-element.md)|定義單一功能表項目。|
|[Combo 元素](../extensibility/combo-element.md)|定義出現在下拉式方塊中的命令。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
