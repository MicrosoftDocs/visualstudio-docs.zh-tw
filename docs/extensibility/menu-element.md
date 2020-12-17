---
title: Menu 元素 |Microsoft Docs
description: Menu 元素會定義一個功能表項目。 功能表的種類為 CoNtext、Menu、MenuController、MenuControllerLatched、Toolbar 和 ToolWindowToolbar。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f20e05c50bf208490edd237299653a3caa6b559f
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616071"
---
# <a name="menu-element"></a>Menu 元素
定義一個功能表項目。 以下是六種功能表：內容、功能表、MenuController、MenuControllerLatched、工具列和 ToolWindowToolbar。

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
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的識別碼。|
|priority|選擇性。 數值，這個值會指定功能表在一組功能表中的相對位置。|
|ToolbarPriorityInBand|選擇性。 數值，這個值會指定當視窗停駐時，該工具列在帶狀線中的相對位置。|
|type|選擇性。 指定元素種類的列舉值。<br /><br /> 如果不存在，則預設類型為 [功能表]。<br /><br /> 內容<br /> 當使用者在視窗上按一下滑鼠右鍵時，所顯示的快捷方式功能表。 快捷方式功能表具有下列特性：<br /><br /> ：當功能表顯示為快捷方式功能表時，不會使用 **父** 欄位和 **優先權** 欄位。<br />-可做為子功能表，也可以當做快捷方式功能表使用。 在此情況下，會遵守 **群組識別碼** 和 **優先權** 欄位。<br />-不一定可以使用。<br /><br /> 只有當下列條件成立時，才會顯示快捷方式功能表：<br /><br /> -主控它的視窗隨即顯示。<br />-VSPackage 中的滑鼠處理常式會偵測到視窗上以滑鼠右鍵按一下，然後呼叫處理命令的方法。<br />-透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 方法 (建議的方法) 或方法來顯示快捷方式功能表 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 。<br /><br /> 功能表<br /> 提供下拉式功能表。 下拉式功能表具有下列特性：<br /><br /> -遵循其定義中的父系。<br />-必須有父群組或群組的 CommandPlacement。<br />-可以是任何其他類型功能表中的子功能表。<br />-會在每次顯示父功能表時自動顯示。<br />-不需要將任何 VSPackage 程式碼實作為顯示。<br /><br /> MenuController<br /> 提供分割按鈕的下拉式功能表，通常用於工具列。 MenuController 功能表具有下列特性：<br /><br /> -必須透過父系或 CommandPlacement 包含在另一個功能表中。<br />-遵循其定義中的父系。<br />-可以有任何類型的功能表做為其父代。<br />-在顯示其父功能表時，會自動成為可用。<br />-不需要以程式設計方式支援來顯示功能表。<br /><br /> [分割] 按鈕功能表中的命令會顯示在功能表按鈕上。 顯示的命令具有下列其中一個特性：<br /><br /> -這是在仍顯示並啟用命令時，所使用的最後一個命令。<br />-這是第一個顯示的命令。<br /><br /> MenuControllerLatched<br /> 提供可透過將命令標示為已鎖定的方式，將命令指定為預設選項的分割按鈕下拉式功能表。<br /><br /> 鎖定的命令是在功能表中標示為已選取的命令，通常是藉由顯示核取記號。 如果命令在介面的方法的執行中有設定 OLECMDF_LATCHED 旗標，則可將命令標示為已鎖定 `QueryStatus` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。 MenuControllerLatched 功能表具有下列特性：<br /><br /> -必須透過父群組或 CommandPlacement 包含在另一個功能表中。<br />-遵循其定義中的父系。<br />-可以有任何類型的功能表做為其父代。<br />-在顯示其父功能表時可供使用。<br />-不需要以程式設計方式支援來顯示功能表。<br /><br /> [分割] 按鈕功能表中的命令會顯示在功能表按鈕上。 顯示的命令具有下列其中一個特性：<br /><br /> -這是已鎖定的第一個顯示命令。<br />-這是第一個顯示的命令。<br /><br /> 工具列<br /> 提供工具列。 工具列具有下列特性：<br /><br /> -忽略其定義中的父系。<br />-不能成為任何群組的子功能表，甚至不能使用 CommandPlacement。<br />-隨時可以按一下 [ **View** ] 功能表上的 [**工具列**] 來顯示。<br />-可以使用 [VisibilityItem](../extensibility/visibilityitem-element.md)來顯示。<br />-不需要任何程式碼就能建立。 如需如何建立工具列的範例，請參閱 [加入工具列](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 提供附加至特定工具視窗的工具列，就如同附加至開發環境的工具列一樣。<br /><br /> -忽略其定義中的父系。<br />-不能成為任何群組的子功能表，甚至不能使用 CommandPlacement。<br />-只有在顯示主控工具列的工具視窗，且 VSPackage 明確地將工具列加入至工具視窗時，才會顯示。 這通常是在建立工具視窗時完成的，方法是取得工具列主控制項屬性 (如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>) 從工具視窗框架表示的介面，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> 方法。|
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父代|選擇性。 功能表項目的父元素。|
|CommandFlag|必要。 請參閱 [命令旗標元素](../extensibility/command-flag-element.md)。 功能表的有效 CommandFlag 值如下：<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -此旗標不會影響工具列的顯示。<br />-   **DontCache**<br />-   **DynamicVisibility** -此旗標不會影響工具列的顯示。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|字串|必要。 請參閱 [Strings 元素](../extensibility/strings-element.md)。 `ButtonText`必須定義子項目。|
|Annotation|選擇性批註。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[Menu 元素](../extensibility/menus-element.md)|定義 VSPackage 所實行的所有功能表。|

## <a name="example"></a>範例

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 命令表格 (. .vsct) 檔](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
