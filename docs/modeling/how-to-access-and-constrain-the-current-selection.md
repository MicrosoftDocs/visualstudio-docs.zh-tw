---
title: 如何：存取及限制目前的選取範圍
description: 瞭解如何在您針對網域指定的語言撰寫命令或軌跡處理常式時，判斷使用者以滑鼠右鍵按一下的元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ba656793b630dd55fc2ebc7242e5d45484b0f8e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363389"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>如何：存取及限制目前的選取範圍

當您針對特定領域語言撰寫命令或軌跡處理常式時，可以決定使用者以滑鼠右鍵按一下的元素。 您也可以防止選取某些圖形或欄位。 例如，您可以安排在使用者按一下圖示裝飾專案時，改為選取包含該專案的圖形。 以這種方式限制選取，可減少您必須撰寫的處理常式數目。 它也可讓使用者更輕鬆地按一下圖形中的任何位置，而不需要避免裝飾專案。

## <a name="access-the-current-selection-from-a-command-handler"></a>從命令處理常式存取目前的選取範圍

特定領域語言的命令集類別包含您自訂命令的命令處理常式。 從中 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 衍生特定領域語言之命令集類別的類別，可提供幾個成員來存取目前的選取範圍。

視命令而定，命令處理常式可能需要在模型設計師、模型 explorer 或使用中視窗中選取。

### <a name="to-access-selection-information"></a>存取選取資訊

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別會定義下列可以用來存取目前選取範圍的成員。

    |member|描述|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 方法|`true`如果模型設計師中選取的任何元素是區間圖形，則傳回，否則傳回 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 方法|`true`如果已在模型設計師中選取圖表，則會傳回，否則會傳回 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 方法|`true`如果模型設計師中只選取一個元素，則傳回，否則為 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 方法|`true`如果在使用中視窗中只選取一個專案，則傳回，否則為 `false` 。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 屬性|取得在模型設計師中選取之元素的唯讀集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 屬性|取得在使用中視窗中選取之元素的唯讀集合。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 屬性|取得模型設計師中選取範圍的主要元素。|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 屬性|取得使用中視窗中選取範圍的主要元素。|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>類別的屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 可讓您存取 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> 代表模型設計師視窗的物件，並提供模型設計師中所選取專案的其他存取權。

3. 此外，所產生的程式碼會針對網域指定的語言，在命令集類別中定義 explorer 工具視窗屬性和 explorer 選取專案屬性。

    - [Explorer] 工具視窗屬性會傳回網域特定語言的 [explorer] 工具視窗類別的實例。 Explorer 工具視窗類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> 類別，並代表特定領域語言的模型瀏覽器。

    - `ExplorerSelection`屬性會在 [模型瀏覽器] 視窗中，針對特定領域語言傳回選取的元素。

## <a name="determine-which-window-is-active"></a>判斷使用中的視窗

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>介面包含定義成員，可讓您存取 shell 中目前的選取狀態。 您可以 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 透過 `MonitorSelection` 每個類別之基類中所定義的屬性，從 package 類別或命令集類別取得物件。 封裝類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> 類別，而且命令集類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 類別。

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>從命令處理常式判斷使用中的視窗類型

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>類別的屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 會傳回 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 物件，此物件可讓您存取 shell 中目前的選取範圍狀態。

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>介面的屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 會取得作用中的選取範圍容器，此容器可能與使用中視窗不同。

3. 將下列屬性新增至網域特定語言的命令集類別，以判斷哪一種視窗處於作用中狀態。

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

藉由新增選取規則，您可以控制當使用者選取模型中的元素時，所要選取的專案。 例如，若要允許使用者將多個元素視為單一單位，您可以使用選取規則。

### <a name="to-create-a-selection-rule"></a>若要建立選取規則

1. 在 DSL 專案中建立自訂程式碼檔案

2. 定義衍生自類別的選取規則類別 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> 。

3. 覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> 選取範圍規則類別的方法，以套用選取準則。

4. 將 ClassDiagram 類別的部分類別定義新增至您的自訂程式碼檔案。

     `ClassDiagram`類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> 類別，並定義于所產生的程式碼檔案（Diagram.cs）中（在 DSL 專案中）。

5. 覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 類別的屬性 `ClassDiagram` ，以傳回自訂選取規則。

     屬性的預設執行 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 會取得未修改選取範圍的選取規則物件。

### <a name="example"></a>範例

下列程式碼檔案會建立一個選取範圍規則，展開選取範圍，以包含一開始選取之每個網域圖形的所有實例。

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