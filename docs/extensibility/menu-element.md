---
title: "功能表項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 58b948e7ec420442eae839cd4eeefbccbe6b509d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="menu-element"></a>功能表項目
定義一個功能表項目。 這些是功能表的六種： 內容、 功能表、 MenuController、 MenuControllerLatched、 工具列和 ToolWindowToolbar。  
  
## <a name="syntax"></a>語法  
  
```  
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼命令識別項的識別碼。|  
|priority|選擇性。 數值，指定群組中的功能表的功能表的相對位置。|  
|ToolbarPriorityInBand|選擇性。 指定的相對位置 工具列的頻外時使用的視窗固定數字值。|  
|類型|選擇性。 列舉的值，指定項目的類型。<br /><br /> 如果不存在，則預設類型是功能表。<br /><br /> 內容<br /> 當使用者按一下滑鼠右鍵視窗會顯示快顯功能表。 快顯功能表具有下列特性：<br /><br /> -不使用父及優先權欄位，顯示為快顯功能表的功能表時。<br />-可做為子功能表，為快顯功能表。 在此情況下，會遵守群組識別碼 和 優先順序 欄位。<br />-這是不是永遠可使用。<br /><br /> 只有當下列條件成立時，會顯示快顯功能表：<br /><br /> 它裝載-視窗隨即顯示。<br />-滑鼠處理常式在 VSPackage 中的偵測到視窗上的按一下滑鼠右鍵，然後再呼叫 處理命令的方法。<br />-的捷徑功能表會顯示藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A>方法 （建議方式） 或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>方法。<br /><br /> 功能表<br /> 提供下拉式選單。 下拉式選單具有下列特性：<br /><br /> -會遵守其定義中的父系。<br />-必須有父群組或 CommandPlacement 至群組。<br />-可以是功能表的任何其他種類中的子功能表。<br />-這是會自動顯示其父功能表顯示時。<br />-不需要任何 VSPackage 程式碼，使其顯示的實作。<br /><br /> MenuController<br /> 提供分割按鈕下拉式選單，通常用於在工具列中。 MenuController 功能表具有下列特性：<br /><br /> -必須包含在父代或 CommandPlacement 透過另一個功能表。<br />-會遵守其定義中的父系。<br />-可以有任何一種功能表做為其父系。<br />-會自動成為可用時就會顯示其父功能表。<br />-不需要以程式設計方式的支援人員以進行顯示的功能表。<br /><br /> 分割按鈕的功能表命令會顯示在 [功能表] 按鈕。 此命令顯示具有下列特性的其中一個：<br /><br /> -如果仍然顯示，而且已啟用命令所使用的最後一個命令它。<br />-它是第一個顯示的命令。<br /><br /> MenuControllerLatched<br /> 提供的命令可以指定為預設選取項目將標示命令，為閂鎖分割按鈕下拉式選單。<br /><br /> 鎖住的命令是通常是藉由顯示核取記號標示為已選取，功能表中的命令。 命令可能會標示為閂鎖是否 OLECMDF_LATCHED 旗標設於實作的`QueryStatus`方法<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 MenuControllerLatched 功能表具有下列特性：<br /><br /> -必須包含在父群組或 CommandPlacement 透過另一個功能表。<br />-會遵守其定義中的父系。<br />-可以有任何一種功能表做為其父系。<br />-這是供顯示其父功能表時。<br />-不需要以程式設計方式的支援人員以進行顯示的功能表。<br /><br /> 分割按鈕的功能表命令會顯示在 [功能表] 按鈕。 此命令顯示具有下列特性的其中一個：<br /><br /> -第一個顯示的命令已閂鎖的它。<br />-它是第一個顯示的命令。<br /><br /> 工具列<br /> 提供的工具列。 工具列上有下列特性：<br /><br /> -會忽略其定義中的父系。<br />-無法透過子功能表中的任何群組中，甚至不能使用 CommandPlacement。<br />-可以一律會顯示依序按一下**工具列**上**檢視**功能表。<br />-可以透過顯示[VisibilityItem](../extensibility/visibilityitem-element.md)。<br />-不需要任何程式碼來建立它。 如需如何建立工具列的範例，請參閱[新增工具列](../extensibility/adding-a-toolbar.md)。<br /><br /> ToolWindowToolbar<br /> 就如同工具列會附加至開發環境，請提供連接到特定的工具視窗中，工具列。<br /><br /> -會忽略其定義中的父系。<br />-無法透過子功能表中的任何群組中，甚至不能使用 CommandPlacement。<br />-這是當顯示裝載工具列的 [工具] 視窗和 VSPackage 明確地加入至 [工具] 視窗工具列顯示。 這通常是藉由取得工具列主機內容建立工具視窗時 (所表示的<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost>介面) 從工具視窗框架，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A>方法。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代|選擇性。 功能表項目的父項目。|  
|CommandFlag|必要。 請參閱[命令旗標的項目](../extensibility/command-flag-element.md)。 CommandFlag 功能表的有效值，如下所示：<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -這個旗標不會影響顯示的工具列。<br />-   **DontCache**<br />-   **DynamicVisibility** -這個旗標不會影響顯示的工具列。<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **文字變更**<br />-   **TextIsAnchorCommand**|  
|字串|必要。 請參閱[字串項目](../extensibility/strings-element.md)。 子系`ButtonText`必須定義項目。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Menus 元素](../extensibility/menus-element.md)|定義所有實作 VSPackage 的功能表。|  
  
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
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)