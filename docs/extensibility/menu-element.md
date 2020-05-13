---
title: 選單元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702604"
---
# <a name="menu-element"></a>選單元素
定義一個功能表項。 它們是六種功能表:上下文、功能表、功能表控制器、功能表控制器、工具列和工具視窗工具列。

## <a name="syntax"></a>語法

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/ID 命令識別碼的 GUID。|
|id|必要。 GUID/ID 命令識別碼的識別碼。|
|priority|選擇性。 指定選單組中選單的相對位置的數值。|
|工具列優先權內帶|選擇性。 在視窗停靠時指定工具列在波段的相對位置的數值。|
|type|選擇性。 指定元素類型的枚舉值。<br /><br /> 如果不存在,則默認類型為"功能表"。<br /><br /> Context<br /> 當用戶右鍵單擊視窗時顯示的快捷功能表。 快捷選單具有以下特徵:<br /><br /> - 當選單顯示為快捷選單時,不使用 **"父**"和 **"優先順序**"欄位。<br />- 可用作子功能表和快捷選單。 在這種情況下,**受遵守組 ID**和**優先順序**欄位。<br />- 並非始終可用。<br /><br /> 只當以下條件為 true 時,才會顯示快捷選單:<br /><br /> - 顯示承載它的視窗。<br />- VSPackage 中的滑鼠處理程序檢測到右鍵按一下視窗,然後調用處理該命令的方法。<br />- 通過調<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A>用 方法(建議的方法)或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>方法來 顯示快捷功能表。<br /><br /> 功能表<br /> 提供下拉菜單。 下拉選單具有以下特徵:<br /><br /> - 在其定義中尊重父項。<br />- 必須具有父組或組的命令放置。<br />- 可以是任何其他種類的功能表中的子功能表。<br />- 每當顯示其父功能表時,都會自動顯示。<br />- 不需要實現任何 VSPackage 代碼來使其顯示。<br /><br /> 選單控制器<br /> 提供拆分按鈕下拉菜單,該功能表通常用於工具列。 選單控制器選單具有以下特徵:<br /><br /> - 必須通過父級或命令放置包含在其他功能表中。<br />- 在其定義中尊重父項。<br />- 可以有任何類型的功能表作為其父功能表。<br />- 只要顯示其父功能表,將自動提供。<br />- 不需要程式設計支援來顯示選單。<br /><br /> 拆分按鈕功能表中的命令將顯示在菜單按鈕上。 顯示的指令具有以下特徵之一:<br /><br /> - 如果該命令仍然顯示並啟用,則使用該命令的最後一個命令。<br />- 這是第一個顯示的命令。<br /><br /> 選單控制器鎖定<br /> 提供拆分按鈕下拉菜單,通過將命令標記為鎖定,可以將命令指定為默認選擇。<br /><br /> 鎖定命令是一個命令,在菜單中標記為所選,通常通過顯示複選標記。 如果命令在`QueryStatus`<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面方法的實現中設置了OLECMDF_LATCHED標誌,則可以將其標記為鎖定。 選單控制器鎖定選單具有以下特徵:<br /><br /> - 必須通過父組或命令放置包含在其他功能表中。<br />- 在其定義中尊重父項。<br />- 可以有任何類型的功能表作為其父功能表。<br />- 只要顯示其父功能表,都可用。<br />- 不需要程式設計支援來顯示選單。<br /><br /> 拆分按鈕功能表中的命令將顯示在菜單按鈕上。 顯示的指令具有以下特徵之一:<br /><br /> - 這是第一個顯示的命令被鎖定。<br />- 這是第一個顯示的命令。<br /><br /> 工具列<br /> 提供工具列。 工具列具有以下特徵:<br /><br /> - 忽略父項的定義。<br />- 不能成為任何組的子功能表,甚至無法使用命令放置。<br />- 始終可以通過按下 **「視圖」** 選單上**的工具列**顯示。<br />- 可以使用[可見性項目](../extensibility/visibilityitem-element.md)顯示 。<br />- 不需要任何代碼來創建它。 有關如何建立工具列的範例,請參閱[新增工具列](../extensibility/adding-a-toolbar.md)。<br /><br /> 工具視窗工具列<br /> 提供附加到特定工具視窗的工具列,就像工具列附加到開發環境一樣。<br /><br /> - 忽略父項的定義。<br />- 不能成為任何組的子功能表,甚至無法使用命令放置。<br />- 僅當顯示承載工具列的工具視窗和 VSPackage 顯式將工具列添加到工具視窗中時,才會顯示。 這通常是通過從工具視窗框架獲取工具列主機屬性(由<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>介面表示)然後調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>方法來創建工具視窗時完成的。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父系|選擇性。 功能表項的父元素。|
|命令旗標|必要。 請參考[指令旗標元素](../extensibility/command-flag-element.md)。 選單的有效命令Flag值如下所示:<br /><br /> -   **始終建立**<br />-   **預設已載**<br />-   **預設不可見**- 此標誌不會影響工具列的顯示。<br />-   **唐特卡奇**<br />-   **動態可見性**- 此標誌不會影響工具列的顯示。<br />-   **圖示與文字**<br />-   **無訂**<br />-   **NOTTBlist**<br />-   **沒有工具列關閉**<br />-   **文字變更**<br />-   **文字 Isanchor 命令**|
|字串|必要。 請參考[字串元素](../extensibility/strings-element.md)。 必須定義`ButtonText`子元素。|
|Annotation|可選註釋。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[選單元素](../extensibility/menus-element.md)|定義 VSPackage 實現的所有功能表。|

## <a name="example"></a>範例

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>AlwaysCreate</CommandFlag>
    <Strings>
      <ButtonText>Edit Widget</ButtonText>
    </Strings>
    </Parent>
</Menu>
```

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
