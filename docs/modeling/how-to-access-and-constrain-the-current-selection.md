---
title: "如何： 存取和限制目前選取範圍 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 81036e04abc9eac2cbed2879839e95cce52166fc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>如何：存取及限制目前的選取範圍
當您為特定領域語言撰寫的命令或軌跡處理常式時，您可以判斷哪些使用者以滑鼠右鍵按一下的項目。 您也可以防止某些圖形或欄位被選取。 例如，您可以排列，當使用者按一下圖示裝飾項目，包含該圖形會改為選取。 限制以這種方式選取範圍減少，您必須撰寫處理常式的數目。 它也讓更方便使用者，使用者可以按一下任何位置圖形中而不需要避免裝飾項目。  
  
## <a name="accessing-the-current-selection-from-a-command-handler"></a>從命令處理常式存取目前的選取範圍  
 特定領域語言的命令集類別包含您的自訂命令的命令處理常式。 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別從中衍生的網域特定定義域語言的命令組類別，提供一些成員，用於存取目前的選取範圍。  
  
 根據命令的命令處理常式可能需要在模型設計師、 模型總管 中或使用中視窗中的選取項目。  
  
#### <a name="to-access-selection-information"></a>若要存取選取項目資訊  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別會定義下列可以用來存取目前的選取範圍的成員。  
  
    |成員|描述|  
    |------------|-----------------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 方法|傳回`true`如果有任何在模型設計師中選取項目是區間圖形; 否則`false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 方法|傳回`true`圖表是選取在模型設計師中; 否則如果`false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 方法|傳回`true`如果只有一個項目是選取在模型設計師中，否則`false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 方法|傳回`true`如果只有一個項目已選取使用中視窗; 否則`false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 屬性|取得在模型設計師中選取之項目的唯讀集合。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 屬性|取得使用中視窗中選取之項目的唯讀集合。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 屬性|取得在模型設計師中的選取項目的的主要項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 屬性|取得使用中視窗的主要選取範圍的項目。|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>屬性<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別提供存取<xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>物件，代表模型設計師視窗，並提供額外的存取在模型設計師中選取的項目。  
  
3.  此外，產生的程式碼定義總管工具視窗屬性，並在命令中的屬性總管 中選擇設定網域特定語言的類別。  
  
    -   總管工具視窗屬性會傳回特定領域語言的總管工具視窗類別的執行個體。 總管工具視窗類別衍生自<xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>類別，並表示模型總管 中的特定領域語言。  
  
    -   `ExplorerSelection`屬性會傳回選取的項目中的特定領域語言 [模型總管] 視窗。  
  
## <a name="determining-which-window-is-active"></a>判斷哪一個視窗作用中  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>介面包含定義可提供存取目前的選取狀態，在介面中的成員。 您可以取得<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>物件在封裝類別或透過網域特定領域語言的命令集類別`MonitorSelection`每個基底類別中定義的屬性。 在封裝類別衍生自<xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>類別，而命令集的類別衍生自<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別。  
  
#### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>若要判斷命令處理常式從何種類型的視窗為作用中  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>屬性<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>類別會傳回<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>提供存取目前的選取狀態，在介面中的物件。  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>屬性<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>介面取得使用中的選取範圍的容器，可以不同於作用中視窗。  
  
3.  加入至命令的下列屬性類別為您設定來判斷哪些類型的視窗為作用中的特定領域語言。  
  
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
  
## <a name="constraining-the-selection"></a>限制 選取項目  
 藉由加入選取規則，您可以控制使用者在模型中選取項目時，會選取哪些項目。 例如，若要允許使用者視為單一單位的項目數目，您可以使用選取範圍規則。  
  
#### <a name="to-create-a-selection-rule"></a>若要建立選取範圍規則  
  
1.  DSL 專案中建立自訂程式碼檔案  
  
2.  定義衍生自的選取範圍規則類別<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>類別。  
  
3.  覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A>選取規則類別，要套用選取準則的方法。  
  
4.  您的自訂程式碼檔案中加入 ClassDiagram 類別的部分類別定義。  
  
     `ClassDiagram`類別衍生自<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>類別，並在產生的程式碼檔案中，Diagram.cs，DSL 專案中定義。  
  
5.  覆寫<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>屬性`ClassDiagram`類別，以傳回自訂選取規則。  
  
     預設實作<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A>屬性會取得不會修改選取項目選取項目規則物件。  
  
### <a name="example"></a>範例  
 下列程式碼檔案建立擴大要包含的每一開始所選取的網域圖形的所有執行個體選取範圍的選取範圍規則。  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>