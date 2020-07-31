---
title: Menu 元素 |Microsoft Docs
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
ms.openlocfilehash: 020098a3026f600629b8ab186431a1d2d5d7795a
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453657"
---
# <a name="menu-element"></a>Menu 元素
定義一個功能表項目。 下列是六種功能表：內容、功能表、MenuController、MenuControllerLatched、工具列和 ToolWindowToolbar。

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

|屬性|說明|
|---------------|-----------------|
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|
|id|必要。 GUID/識別碼命令識別碼的 ID。|
|priority|選擇性。 數值，指定功能表群組中功能表的相對位置。|
|ToolbarPriorityInBand|選擇性。 數值，指定視窗停駐時，工具列在寬線中的相對位置。|
|type|選擇性。 指定元素類型的列舉值。<br /><br /> 如果不存在，預設類型為 [功能表]。<br /><br /> Context<br /> 當使用者以滑鼠右鍵按一下視窗時所顯示的快捷方式功能表。 快捷方式功能表具有下列特性：<br /><br /> -當功能表要顯示為快捷方式功能表時，不會使用 [**父系**] 和 [**優先順序**] 欄位。<br />-可用來做為子功能表，也可以做為快捷方式功能表。 在此情況下，會遵守**群組識別碼**和**優先順序**欄位。<br />-不一定是可用的。<br /><br /> 只有在下列條件成立時，才會顯示快捷方式功能表：<br /><br /> -會顯示裝載它的視窗。<br />-VSPackage 中的滑鼠處理常式會偵測到以滑鼠右鍵按一下視窗，然後呼叫處理命令的方法。<br />-藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 方法（建議的方法）或方法來顯示快捷方式功能表 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 。<br /><br /> 功能表<br /> 提供下拉式功能表。 下拉式功能表具有下列特性：<br /><br /> -遵循其定義中的父系。<br />-必須擁有父群組，或群組的 CommandPlacement。<br />-可以是任何其他類型功能表中的子功能表。<br />-每當顯示其父功能表時，就會自動顯示。<br />-不需要執行任何 VSPackage 程式碼，就能讓它顯示。<br /><br /> MenuController<br /> 提供 [分割按鈕] 下拉式功能表，此功能表通常用於工具列中。 [MenuController] 功能表具有下列特性：<br /><br /> -必須包含在透過父系或 CommandPlacement 的另一個功能表中。<br />-遵循其定義中的父系。<br />-可以有任何類型的功能表作為其父系。<br />-在顯示其父功能表時，會自動成為可用。<br />-不需要以程式設計方式支援來顯示功能表。<br /><br /> [分割] 按鈕功能表中的命令會顯示在功能表按鈕上。 顯示的命令具有下列其中一種特性：<br /><br /> -如果仍然顯示並啟用命令，這是最後一個使用的命令。<br />-這是第一個顯示的命令。<br /><br /> MenuControllerLatched<br /> 提供一個 [分割] 按鈕下拉式功能表，可將命令標示為鎖定，將命令指定為預設選取專案。<br /><br /> 已鎖定的命令是在功能表中標示為已選取的命令，通常是藉由顯示核取記號。 如果命令在介面的方法執行中設定了 OLECMDF_LATCHED 旗標，則可以將它標示為鎖定 `QueryStatus` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。 [MenuControllerLatched] 功能表具有下列特性：<br /><br /> -必須包含在父群組或 CommandPlacement 的另一個功能表中。<br />-遵循其定義中的父系。<br />-可以有任何類型的功能表作為其父系。<br />-可在每次顯示其父功能表時提供使用。<br />-不需要以程式設計方式支援來顯示功能表。<br /><br /> [分割] 按鈕功能表中的命令會顯示在功能表按鈕上。 顯示的命令具有下列其中一種特性：<br /><br /> -這是第一個已鎖定的已顯示命令。<br />-這是第一個顯示的命令。<br /><br /> 工具列<br /> 提供工具列。 工具列具有下列特性：<br /><br /> -忽略其定義中的父系。<br />-不能設為任何群組的子功能表，甚至無法使用 CommandPlacement。<br />-一律可以按一下 [ **View** ] 功能表上的 [**工具列**] 來顯示。<br />-可以使用[VisibilityItem](../extensibility/visibilityitem-element.md)來顯示。<br />-不需要任何程式碼就能建立它。 如需如何建立工具列的範例，請參閱[新增工具列](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 提供附加至特定工具視窗的工具列，就如同將工具列附加至開發環境一樣。<br /><br /> -忽略其定義中的父系。<br />-不能設為任何群組的子功能表，甚至無法使用 CommandPlacement。<br />-只有在顯示裝載工具列的工具視窗時才會顯示，而且 VSPackage 會明確地將工具列新增至工具視窗。 這通常是在建立工具視窗時完成，方法是從工具視窗框架取得工具列主機屬性（由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 介面表示），然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> 方法。|
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|說明|
|-------------|-----------------|
|父系|選擇性。 功能表項目的父元素。|
|CommandFlag|必要。 請參閱[命令旗標元素](../extensibility/command-flag-element.md)。 功能表的有效 CommandFlag 值如下所示：<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -此旗標不會影響工具列的顯示。<br />-   **DontCache**<br />-   **DynamicVisibility** -此旗標不會影響工具列的顯示。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|
|字串|必要。 請參閱[字串元素](../extensibility/strings-element.md)。 `ButtonText`必須定義子項目。|
|Annotation|選擇性批註。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[功能表元素](../extensibility/menus-element.md)|定義 VSPackage 所實行的所有功能表。|

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
- [Visual Studio 命令資料表（. .vsct）檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
