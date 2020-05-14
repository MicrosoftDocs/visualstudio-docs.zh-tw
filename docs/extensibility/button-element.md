---
title: 按鈕元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739936"
---
# <a name="button-element"></a>按鈕項目
定義用戶可以與之交互的元素。 按鈕可以是不同類型的:按鈕、功能表按鈕和拆分下拉。

## <a name="syntax"></a>語法

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
|guid|必要。 GUID/ID 命令識別碼的 GUID。|
|id|必要。 GUID/ID 命令識別碼的識別碼。|
|priority|選擇性。 指定優先權的數值。|
|type|選擇性。 指定按鈕類型的枚舉值。<br /><br /> 如果未給出,則使用按鈕。<br /><br /> 按鈕<br /> 出現在工具列(通常作為標誌性按鈕)、功能表和上下文菜單上的標準命令。<br /><br /> 選單按鈕<br /> 不執行命令但生成其他功能表的功能表項。<br /><br /> 分割下拉<br /> 控制項,如 Microsoft Word 中標準工具列上的「復原」和「重做」按鈕。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[父元素](../extensibility/parent-element.md)|選擇性。 按鈕的父元素。|
|[圖示元素](../extensibility/icon-element.md)|選擇性。 與按鈕關聯的圖示。|
|[命令旗標元素](../extensibility/command-flag-element.md)|必要。 按鈕的有效命令 Flag 值如下所示。<br /><br /> - 允許帕姆斯<br /><br /> - 命令井只<br /><br /> - 預設關閉<br /><br /> - 預設不可見<br /><br /> - 唐特卡奇<br /><br /> - 動態項目啟動<br /><br /> - 動態可見度<br /><br /> - 修復選單控制器<br /><br /> - 圖示與文字<br /><br /> - 無按鈕定制<br /><br /> - 無訂<br /><br /> - 無鍵定制<br /><br /> - 無秀門控制器<br /><br /> - 皮克特<br /><br /> - 郵政執行<br /><br /> - 普羅維姆姆德<br /><br /> - 路由到文件<br /><br /> - 文字級聯<br /><br /> - 文字選單使用按鈕<br /><br /> - 文字變更<br /><br /> - 文字變更按鈕<br /><br /> - 文字內文使用按鈕<br /><br /> - 文字選單Ctrluse選單<br /><br /> - 文字選單使用按鈕<br /><br /> - 僅文字|
|[字串元素](../extensibility/strings-element.md)|必要。 必須定義子[按鍵文字元素](../extensibility/buttontext-element.md)。|
|Annotation|可選註釋。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[按鈕項目](../extensibility/buttons-element.md)|對按鈕元素進行分組。|

## <a name="example"></a>範例
 下面的範例定義 *.vsct*檔案中的按鈕。

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
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
