---
title: HOW TO：存取及限制目前的選取範圍
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cc93f276dae3caeec08a21a74e3bdcaa365fee9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993455"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>HOW TO：存取及限制目前的選取範圍

當您撰寫您的網域特定語言的命令或軌跡處理常式時，您可以判斷哪些使用者以滑鼠右鍵按一下的項目。 您也可以防止某些圖形或欄位被選取。 例如，您可以排列，當使用者按一下圖示裝飾項目，包含它的形狀會改為選取。 限制這種方式中的選取範圍減少，您必須撰寫處理常式。 它也會讓您更輕鬆的使用者，可以按一下任何位置中的圖形而不需要避免裝飾項目。

## <a name="access-the-current-selection-from-a-command-handler"></a>從命令處理常式存取目前的選取範圍

特定領域語言的命令集類別包含您的自訂命令的命令處理常式。 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別，從特定領域語言的命令集類別衍生，提供一些成員，以存取目前的選取範圍。

根據命令，命令處理常式可能需要在模型設計師、 模型總管 中或使用中視窗中的選取項目。

### <a name="to-access-selection-information"></a>若要存取選取項目資訊

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別會定義下列可用來存取目前的選取範圍的成員。

    |成員|描述|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 方法|傳回`true`是否有任何項目在模型設計師中選取區間圖形; 否則`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 方法|傳回`true`圖表會在模型設計師中選取; 否則如果`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 方法|傳回`true`如果只有一個項目是在模型設計師中選取; 否則即為`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 方法|傳回`true`只有一個項目是否已選取使用中視窗; 否則即為`false`。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 屬性|取得在模型設計師中選取項目的唯讀集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 屬性|取得使用中視窗中選取項目的唯讀集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 屬性|取得在模型設計師中的選取範圍的主要項目。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 屬性|取得選取範圍的主要項目使用中視窗。|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>的屬性<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別提供存取<xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>物件，代表模型設計師視窗，並在模型設計師中選取的項目提供額外的存取權。

3. 此外，產生的程式碼定義總管工具視窗的屬性，並在命令中的檔案總管選取項目屬性設定為網域特定語言的類別。

    - Explorer 工具視窗的屬性會傳回特定領域語言總管工具視窗類別的執行個體。 Explorer 工具視窗類別衍生自<xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>類別，並代表特定領域語言的 [模型總管]。

    - `ExplorerSelection`屬性會傳回選取的項目中針對定義域專屬語言的 [模型總管] 視窗。

## <a name="determine-which-window-is-active"></a>判斷哪一個視窗是作用中

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>介面包含定義提供存取目前的選取狀態，在殼層中的成員。 您可以取得<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>物件在封裝類別或特定領域語言，透過命令集類別`MonitorSelection`每個基底類別中定義的屬性。 封裝類別衍生自<xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>類別和命令集類別衍生自<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別。

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>決定在何種視窗是作用中的命令處理常式

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>的屬性<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別會傳回<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>提供存取目前的選取狀態，在殼層中的物件。

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>屬性<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>介面取得作用中選取範圍容器，這可能會不同於作用中視窗。

3. 新增下列屬性，此命令集類別為您特定領域語言，來判斷何種視窗是作用中。

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>限制的選取範圍

藉由新增選取規則，您可以控制使用者在模型中選取項目時，會選取的項目。 比方說，若要允許使用者的項目數目視為單一單位，您可以使用選取的規則。

### <a name="to-create-a-selection-rule"></a>若要建立選取項目規則

1. 在 DSL 專案中建立自訂程式碼檔案

2. 定義選取範圍規則類別衍生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>類別。

3. 覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A>選取規則類別，要套用選取準則的方法。

4. 您的自訂程式碼檔案中加入 ClassDiagram 類別的部分類別定義。

     `ClassDiagram`類別衍生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>類別，並在產生的程式碼檔案中，Diagram.cs，在 DSL 專案中定義。

5. 覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>屬性`ClassDiagram`類別，以傳回自訂的選取範圍規則。

     預設實作<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>屬性會取得不會修改選取項目選取項目規則物件。

### <a name="example"></a>範例

下列程式碼檔案建立選取範圍規則可展開以包含所有執行個體一開始所選取的網域圖形的每個選取項目。

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>