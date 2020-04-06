---
title: 組合元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739814"
---
# <a name="combo-element"></a>組合項目
定義顯示在組合框中的命令。 組合框有四種,如下所示:下拉康博、動態康波、指數康博和MRUCombo。

## <a name="syntax"></a>語法

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
|guid|必要。 GUID/ID 命令識別碼的 GUID。|
|id|必要。 GUID/ID 命令識別碼的識別碼。|
|預設寬度|必要。 指定組合框圖元寬度的整數。|
|id 命令清單|必要。 發送到活動命令目標的 ID,用於檢索要在組合框中顯示的專案清單。 ID 將與控制項位於相同的 GUID 作用域中。|
|priority|選擇性。 指定優先權的數值。|
|type|選擇性。 指定按鈕類型的枚舉值。<br /><br /> 如果未給出,則使用按鈕。<br /><br /> 下拉康博<br /> VS包裝負責填寫此組合框的內容。 使用者無法在此下拉清單的文本框中鍵入任何內容。<br /><br /> 動態通信<br /> VS包裝負責填寫此組合框的內容。 用戶可以編輯此組合,也可以選擇其中的專案。<br /><br /> 索引孔博<br /> 與 DynamicCombo 相同,只不過它提高了項的索引,而不是其文本。<br /><br /> MRUCombo<br /> 由代表 VSPackage 的整合式開發環境 (IDE) 填充。  用戶可以在此組合框中進行編輯。 IDE 最多記住每個組合框的最後 16 個條目。<br /><br /> 當使用者在組合框中選擇某些內容或輸入新內容時,IDE 會通知相應的 VSPackage。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父系|選擇性。 按鈕的父元素。|
|命令旗標|必要。 請參考[指令旗標元素](../extensibility/command-flag-element.md)。 按鈕的有效命令 Flag 值如下所示。<br /><br /> - 區分大小寫<br /><br /> - 命令井只<br /><br /> - 預設關閉<br /><br /> - 預設不可見<br /><br /> - 動態可見度<br /><br /> - 過濾器鍵<br /><br /> - 圖示與文字<br /><br /> - 無自動完成<br /><br /> - 無按鈕定制<br /><br /> - 無訂<br /><br /> - 無鍵定制<br /><br /> - 橫向拉伸|
|字串|必要。 請參考[字串元素](../extensibility/strings-element.md)。 必須定義子按鈕文本元素。|
|Annotation|可選註釋。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|

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
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
