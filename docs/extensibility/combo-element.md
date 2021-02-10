---
title: 組合元素 |Microsoft Docs
description: 組合元素會定義出現在下拉式方塊中的命令。 有四種類型： DropDownCombo、DynamicCombo、IndexCombo 和 MRUCombo。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc495727fd06bec0d20cab25a7cd8c4716bcc19e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938378"
---
# <a name="combo-element"></a>組合元素
定義出現在下拉式方塊中的命令。 下拉式方塊有四種類型，如下所示： DropDownCombo、DynamicCombo、IndexCombo 和 MRUCombo。

## <a name="syntax"></a>Syntax

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的識別碼。|
|defaultWidth|必要。 指定下拉式方塊之圖元寬度的整數。|
|idCommandList|必要。 傳送至使用中命令目標的識別碼，以取得要顯示在下拉式方塊中的專案清單。 此識別碼將會在與控制項相同的 GUID 範圍中。|
|priority|選擇性。 指定優先權的數位值。|
|類型|選擇性。 指定按鈕類型的列舉值。<br /><br /> 如果未指定，會使用按鈕。<br /><br /> DropDownCombo<br /> VSPackage 負責填入此下拉式方塊的內容。 使用者無法在這個下拉式清單的文字方塊中輸入任何內容。<br /><br /> DynamicCombo<br /> VSPackage 負責填入這個下拉式方塊的內容。 使用者可以編輯這個下拉式方塊，也可以選取其中的專案。<br /><br /> IndexCombo<br /> 與 DynamicCombo 相同，不同之處在于它會引發專案的索引，而不是其文字。<br /><br /> MRUCombo<br />  (IDE) 代表 VSPackage 填入整合式開發環境。  使用者可以在此下拉式方塊中編輯。 IDE 會記住每個下拉式方塊最多最後16個專案。<br /><br /> 當使用者在下拉式方塊中選取某個內容，或輸入新的內容時，IDE 會通知適當的 VSPackage。|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父代|選擇性。 按鈕的父元素。|
|CommandFlag|必要。 請參閱 [命令旗標元素](../extensibility/command-flag-element.md)。 按鈕的有效 CommandFlag 值如下所示。<br /><br /> -CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> -篩選<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|字串|必要。 請參閱 [Strings 元素](../extensibility/strings-element.md)。 必須定義子 ButtonText 元素。|
|Annotation|選擇性批註。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[命令元素](../extensibility/commands-element.md)|代表 VSPackage 工具列上的命令集合。|

## <a name="example"></a>範例

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
