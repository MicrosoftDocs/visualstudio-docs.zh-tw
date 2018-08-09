---
title: 功能表項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d69a6951cdae84ba2abc06bcdfde19fffa665c03
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637506"
---
# <a name="menu-element"></a>功能表項目
定義一個功能表項目。 這些是功能表的六種： 內容、 功能表、 MenuController、 MenuControllerLatched、 工具列和 ToolWindowToolbar。  
  
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
|id|必要。 GUID/識別碼的命令識別項的識別碼。|  
|priority|選擇性。 數值資料類型，用指定的功能表群組中的功能表的相對位置。|  
|ToolbarPriorityInBand|選擇性。 數值資料類型，用停駐視窗時，群組列中指定工具列的相對位置。|  
|類型|選擇性。 列舉的值，指定元素的類型。<br /><br /> 如果不存在，則預設型別是功能表。<br /><br /> 內容<br /> 當使用者按一下滑鼠右鍵 視窗會顯示快顯功能表。 快顯功能表具有下列特性：<br /><br /> -不會使用**父代**並**優先順序**欄位顯示為快顯功能表的功能表時。<br />-可以當做子功能表和捷徑功能表的方式使用。 在此情況下，兩者**群組識別碼**並**優先順序**欄位會遵守。<br />-這是不是永遠可使用。<br /><br /> 僅當下列條件成立時，會顯示快顯功能表：<br /><br /> -裝載它的視窗隨即顯示。<br />-A 滑鼠處理常式，在 VSPackage 中的偵測到視窗上的按一下滑鼠右鍵，然後再呼叫處理命令的方法。<br />-快顯功能表會顯示藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A>方法 （建議） 或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>方法。<br /><br /> 功能表<br /> 提供下拉式選單。 下拉式選單具有下列特性：<br /><br /> -會遵守其定義中的父系。<br />-必須有父群組或 CommandPlacement 至群組。<br />-可以是功能表的任何其他種類中的子功能表。<br />-這是會自動顯示其父功能表顯示時。<br />-不需要任何的 VSPackage 程式碼，即可顯示它的實作。<br /><br /> MenuController<br /> 提供分割按鈕下拉式選單，這通常會在工具列中。 MenuController 功能表具有下列特性：<br /><br /> -必須包含在父代或 CommandPlacement 透過另一個功能表。<br />-會遵守其定義中的父系。<br />-可以有任何一種功能表做為其父系。<br />-會自動成為可用時就會顯示其父功能表。<br />-不需要程式設計的支援，要顯示的功能表。<br /><br /> 從分割按鈕的功能表命令會顯示在 [功能表] 按鈕。 顯示命令有下列特性的其中一個：<br /><br /> -它是最後一個命令仍會顯示，並且啟用已使用的命令。<br />-它是第一個顯示的命令。<br /><br /> MenuControllerLatched<br /> 提供分割按鈕下拉式選單中的命令可以指定為預設選取項目來標記的命令，因為閂鎖。<br /><br /> 鎖住的命令是通常是藉由顯示核取記號標示已選取功能表中的命令。 命令可以標示為閂鎖是否 OLECMDF_LATCHED 上設定它的實作中的旗標`QueryStatus`方法的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 MenuControllerLatched 功能表具有下列特性：<br /><br /> -必須包含在父群組或 CommandPlacement 透過另一個功能表。<br />-會遵守其定義中的父系。<br />-可以有任何一種功能表做為其父系。<br />-這是可顯示其父功能表時。<br />-不需要程式設計的支援，要顯示的功能表。<br /><br /> 從分割按鈕的功能表命令會顯示在 [功能表] 按鈕。 顯示命令有下列特性的其中一個：<br /><br /> -它是已閂鎖的第一個顯示的命令。<br />-它是第一個顯示的命令。<br /><br /> 工具列<br /> 提供的工具列。 工具列具有下列特性：<br /><br /> -忽略其定義中的父系。<br />-無法建立子功能表中的任何群組，甚至不是藉由使用 CommandPlacement。<br />-可以一律會顯示依序按一下**工具列**上**檢視**功能表。<br />-可以使用來顯示[VisibilityItem](../extensibility/visibilityitem-element.md)。<br />-不需要任何程式碼來建立它。 如需如何建立工具列的範例，請參閱 <<c0> [ 新增工具列](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 就像工具列是開發環境，請提供連接至特定的工具視窗中，工具列。<br /><br /> -忽略其定義中的父系。<br />-無法建立子功能表中的任何群組，甚至不是藉由使用 CommandPlacement。<br />-這被顯示只有在裝載工具列的 [工具] 視窗會顯示，而 VSPackage 明確地將工具列新增至 [工具] 視窗。 這通常是建立工具視窗取得工具列的 [主機] 屬性時 (表示的<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>介面) 工具視窗框架，然後呼叫從<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>方法。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代|選擇性。 功能表項目的父項目。|  
|CommandFlag|必要。 請參閱[Command flag 元素](../extensibility/command-flag-element.md)。 針對功能表的有效 CommandFlag 值如下所示：<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -這個旗標不會影響顯示的工具列。<br />-   **DontCache**<br />-   **DynamicVisibility** -這個旗標不會影響顯示的工具列。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **文字變更**<br />-   **TextIsAnchorCommand**|  
|字串|必要。 請參閱[Strings 元素](../extensibility/strings-element.md)。 子系`ButtonText`必須定義項目。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[功能表項目](../extensibility/menus-element.md)|定義實作 VSPackage 的所有功能表。|  
  
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
 [Visual Studio 命令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)