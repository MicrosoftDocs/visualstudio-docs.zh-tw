---
title: Button 元素 |Microsoft Docs
description: 按鈕專案會定義使用者可以與之互動的元素。 按鈕可以是不同的類型： Button、MenuButton 和 SplitDropDown。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec0640313195d6a15599d1a765081557c0c1a75a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068138"
---
# <a name="button-element"></a>Button 元素
定義使用者可以與之互動的元素。 按鈕可以是不同的類型： Button、MenuButton 和 SplitDropDown。

## <a name="syntax"></a>Syntax

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的識別碼。|
|priority|選擇性。 指定優先權的數位值。|
|類型|選擇性。 指定按鈕種類的列舉值。<br /><br /> 如果未指定，會使用按鈕。<br /><br /> 按鈕<br /> 出現在工具列上的標準命令 (通常是 iconic 按鈕) 、功能表和內容功能表。<br /><br /> MenuButton<br /> 不會執行命令，但是會產生另一個功能表的功能表項目。<br /><br /> SplitDropDown<br /> 控制項，例如 Microsoft Word 中標準工具列上的 [復原] 和 [重做] 按鈕。|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[父元素](../extensibility/parent-element.md)|選擇性。 按鈕的父元素。|
|[Icon 元素](../extensibility/icon-element.md)|選擇性。 與按鈕相關聯的圖示。|
|[命令旗標元素](../extensibility/command-flag-element.md)|必要。 按鈕的有效 CommandFlag 值如下所示。<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextCoNtextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|
|[Strings 元素](../extensibility/strings-element.md)|必要。 必須定義子 [ButtonText 元素](../extensibility/buttontext-element.md) 。|
|Annotation|選擇性批註。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[按鈕元素](../extensibility/buttons-element.md)|群組按鈕元素。|

## <a name="example"></a>範例
 下列範例會在 *.vsct* 檔案中定義一個按鈕。

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
