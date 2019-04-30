---
title: 字串項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de2ed5d9c757d9082cd06c2aae5a8e51b0865714
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432378"
---
# <a name="strings-element"></a>Strings 項目
字串項目必須包含至少一個**ButtonText**子項目。 所有其他子項目是選擇性的。 無效的 XML 字元，例如 '&' 和 '<' 必須編碼為實體 ('&amp;'和'&lt;' 等)。

 連字號文字字串中的指定命令的鍵盤快速鍵。

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
|語言|選擇性。 Language ="。"。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|ButtonText|此欄位和命令定義五個以下的文字欄位可讓您指定各種功能表所顯示的文字。 根據預設，`ButtonText`欄位會出現在功能表控制站。 `ButtonText`欄位也會變成預設值，如果其他的文字欄位為空白。 `ButtonText`欄位不可為空白，即使指定的其他文字欄位。|
|ToolTipText|`ToolTipText`欄位會指定功能表項目的工具提示中所顯示的文字。<br /><br /> 如果`ToolTipText`欄位為空白，`ButtonText`欄位使用。|
|MenuText|`MenuText`欄位會指定是否在主功能表中，工具列上，在快顯功能表中，或在子功能表上，命令會顯示的文字。 如果`MenuText`欄位為空白、 整合式的開發環境 (IDE) 使用`ButtonText`欄位。 `MenuText`欄位也可以用於當地語系化。<br /><br /> 針對捷徑功能表，`MenuText`欄位是顯示在快顯功能表工具列中，可讓在 IDE 中的捷徑功能表的自訂名稱。 因此，指明在您命名您的快顯功能表;例如，使用 「 小工具封裝捷徑功能表 」 取代 「 快速鍵 」。<br /><br /> 如果`MenuText`未指定欄位，`ButtonText`欄位使用。|
|CommandName|`CommandName`欄位會指定在的 [鍵盤] 類別中所顯示的文字**命令**索引標籤**自訂**對話方塊中 (您可以按一下**自訂**上**工具**功能表)。|
|CanonicalName|英文`CanonicalName`欄位在英文中輸入的文字中指定的命令名稱**命令**視窗來執行的功能表項目。 IDE 會去除不是字母、 數字、 底線或內嵌的句號的任何字元。 這段文字然後串連以`ButtonText`欄位來定義命令。 例如，**新的專案**上**檔案**功能表會變成 File.NewProject 命令。<br /><br /> 如果英文`CanonicalName`未指定欄位時，IDE 會使用`ButtonText`欄位和帶狀線出所有除了字母、 數字、 底線和內嵌的句號。 例如，按鈕的文字"& 定義命令..."會變成的 DefineCommands，移除連字號、 空格，然後省略符號。<br /><br /> 如果`TextChanges`指定旗標和命令的文字會變更，可辨識的對應命令**命令** 視窗不會變更，它會保留原始的標準格式`ButtonText`或英文`CanonicalName`欄位。|
|LocCanonicalName|`LocCanonicalName`欄位目的行為完全相同的英文`CanonicalName`欄位但可讓指定的當地語系化的命令文字。 您可以指定兩個標準欄位。 因為 IDE 只會剖析輸入的文字**命令**視窗，並將它與命令，以英文和非英文文字可以是相同的命令相關聯。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[Button 元素](../extensibility/button-element.md)|定義使用者可以互動的項目。|
|[Menu 元素](../extensibility/menu-element.md)|定義單一功能表項目。|
|[Combo 元素](../extensibility/combo-element.md)|定義會出現在下拉式方塊中的命令。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)