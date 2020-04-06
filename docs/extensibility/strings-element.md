---
title: 字串元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699724"
---
# <a name="strings-element"></a>Strings 項目
字串元素必須至少包含一個**ButtonText**子元素。 所有其他子元素都是可選的。 無效的 XML 字元(如"&"和"<")必須編&amp;碼為 實體(''和''&lt;等)。

 文字字串中的 ampersand 指定命令的鍵盤快捷方式。

## <a name="syntax"></a>語法

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
|語言|選擇性。 語言="|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|按鈕文字|此欄位與指令定義的以下五個文字欄位允許您指定出現在各種選單中的文字。 預設情況下,該`ButtonText`欄位將顯示在菜單控制器中。 如果`ButtonText`其他文本欄位為空,則該欄位也將成為預設值。 即使`ButtonText`指定了其他文本欄位,該欄位也不能為空。|
|工具提示文字|該`ToolTipText`欄位指定選單的工具提示中顯示的文字。<br /><br /> 如果`ToolTipText`該欄位為空,`ButtonText`則使用該欄位。|
|選單文字|如果`MenuText`命令位於主選單、工具列、快捷功能表或子選單中,則該欄位指定為命令顯示的文本。 如果`MenuText`欄位為空,則整合式開發環境 (IDE) 使用`ButtonText`該欄位。 該`MenuText`欄位還可用於當地語系化。<br /><br /> 對於快捷選單,該`MenuText`欄位是「快捷功能表」工具列中顯示的名稱,該工具列允許自定義 IDE 中的快捷功能表。 因此,在快捷功能表的名稱中具體說明;例如,使用「小工具包快捷功能表」而不是「快捷方式」。<br /><br /> 如果未指定`MenuText`該欄位,則使用`ButtonText`該 欄位。|
|命令名稱|這個`CommandName`欄位指定 **「 自訂」** 對話方塊中 **「指令」** 選項卡中鍵盤類別中顯示的文字(可透過按下'**工具**「選單上的 **」自訂**「來提供)。|
|CanonicalName|英語`CanonicalName`欄位在英文文字中指定命令的名稱,該命令可以在 **「命令」** 視窗中輸入以執行選單項。 IDE 會剝離不是字母、數位、下劃線或嵌入句點的任何字元。 然後,將此文字串聯到欄位以`ButtonText`定義命令。 例如 **,「** 選單上 **」新專案**「將成為命令 File.NewProject。<br /><br /> 如果未指定英語`CanonicalName`欄位,IDE 將`ButtonText`使用該欄位,並剝離除字母、數位、下劃線和嵌入句點之外的所有句點。 例如,按鈕文本"&定义命令..."變為 DefineCommands,其中刪除安培、空格和橢圓。<br /><br /> 如果指定`TextChanges`了標誌並更改了命令的文本,**則命令**視窗識別的相應命令不會更改;如果指定了該標誌,並且更改了命令視窗的文本。"它仍然是原始`ButtonText`或`CanonicalName`英語 欄位的規範形式。|
|Loccanonon 名稱|欄位`LocCanonicalName`與`CanonicalName`英文欄位行為相同,但允許指定當地語系化的命令文本。 可以指定兩個規範欄位。 由於 IDE 只是分析在**命令**視窗中輸入的文本並將其與命令相關聯,因此英語和非英語文本都可以與同一命令相關聯。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[Button 元素](../extensibility/button-element.md)|定義用戶可以與之交互的元素。|
|[Menu 元素](../extensibility/menu-element.md)|定義單個功能表項。|
|[Combo 元素](../extensibility/combo-element.md)|定義顯示在組合框中的命令。|

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
