---
title: 如何：存取及限制目前的選取範圍
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1f5aaa106e00f9b10eb88892bcc978b92a01c79
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545687"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>如何：存取及限制目前的選取範圍

當您針對網域指定的語言撰寫命令或軌跡處理常式時，您可以決定使用者以滑鼠右鍵按一下哪個元素。 您也可以防止選取某些圖形或欄位。 例如，您可以在使用者按一下圖示裝飾專案時進行排列，改為選取包含它的圖形。 以這種方式限制選取，可減少您必須撰寫的處理常式數目。 它也可以讓使用者更輕鬆地按一下圖形中的任何位置，而不必避免裝飾專案。

## <a name="access-the-current-selection-from-a-command-handler"></a>從命令處理常式存取目前的選取範圍

特定領域語言的命令集類別包含您自訂命令的命令處理常式。 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別，這是定義域特定語言所衍生的命令集類別，它會提供幾個成員來存取目前的選取範圍。

視命令而定，命令處理常式可能需要模型設計師、模型瀏覽器或使用中視窗中的選取專案。

### <a name="to-access-selection-information"></a>存取選取資訊

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別會定義可用於存取目前選取範圍的下列成員。

    |member|描述|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 方法|`true`如果在模型設計師中選取的任何元素為區間圖形，則傳回，否則傳回 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 方法|`true`如果在模型設計師中選取圖表，則傳回，否則傳回 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 方法|`true`如果在模型設計師中只選取一個專案，則傳回，否則傳回 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 方法|`true`如果在使用中視窗中只選取一個專案，則傳回，否則傳回 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 屬性|取得在模型設計師中選取之元素的唯讀集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 屬性|取得在使用中視窗中選取之元素的唯讀集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 屬性|取得模型設計師中選取範圍的主要元素。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 屬性|取得使用中視窗中選取範圍的主要元素。|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>類別的屬性（property） <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 可讓您存取 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> 代表模型設計師視窗的物件，並在模型設計師中提供其他存取所選取之元素的許可權。

3. 此外，所產生的程式碼會針對網域指定的語言，在命令集類別中定義 [explorer 工具視窗] 屬性和 [explorer 選取範圍] 屬性。

    - [Explorer 工具視窗] 屬性會針對網域指定的語言，傳回 explorer 工具視窗類別的實例。 Explorer 工具視窗類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> 類別，並代表特定領域語言的模型瀏覽器。

    - `ExplorerSelection`屬性會針對特定領域語言，傳回 [模型 explorer] 視窗中選取的專案。

## <a name="determine-which-window-is-active"></a>判斷作用中的視窗

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>介面包含定義成員，可讓您存取 shell 中目前的選取範圍狀態。 您可以 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 透過 `MonitorSelection` 每個的基類中所定義的屬性，從 package 類別或命令集類別取得特定領域語言的物件。 封裝類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> 類別，而命令集類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 類別。

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>從命令處理常式判斷作用中的視窗類型

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>類別的屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 會傳回 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 物件，以提供對 shell 中目前選取範圍狀態的存取。

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>介面的屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 會取得使用中的選取容器，這可能與使用中視窗不同。

3. 將下列屬性新增至您的網域特定語言的命令集類別，以判斷作用中的視窗類型。

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

## <a name="constrain-the-selection"></a>限制選取範圍

藉由加入選取規則，您可以控制當使用者選取模型中的元素時，所要選取的元素。 例如，若要讓使用者將數個元素視為單一單位，您可以使用選取範圍規則。

### <a name="to-create-a-selection-rule"></a>建立選取範圍規則

1. 在 DSL 專案中建立自訂程式碼檔案

2. 定義衍生自類別的選取範圍規則類別 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> 。

3. 覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> 選取範圍規則類別的方法，以套用選取準則。

4. 將 ClassDiagram 類別的部分類別定義加入至您的自訂程式碼檔案。

     `ClassDiagram`類別衍生自類別， <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> 並定義于 DSL 專案中產生的程式碼檔案（Diagram.cs）中。

5. 覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 類別的屬性 `ClassDiagram` ，以傳回自訂選取範圍規則。

     屬性的預設執行 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 會取得不會修改選取範圍的選取範圍規則物件。

### <a name="example"></a>範例

下列程式碼檔案會建立展開選取範圍的選取範圍規則，以包含一開始選取之每個網域圖形的所有實例。

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