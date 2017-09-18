---
title: "如何：存取及限制目前的選取範圍 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 存取目前的選取範圍"
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 14
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 14
---
# 如何：存取及限制目前的選取範圍
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您為網域特定語言撰寫的命令或軌跡處理常式時，您可以判斷哪些使用者以滑鼠右鍵按一下的項目。 您也可以防止某些圖形或欄位被選取。 例如，您可以排列，當使用者按一下圖示裝飾項目，包含該圖形會改為選取。 條件約束以這種方式選取項目減少，您必須撰寫處理常式。 它也可方便使用者，可以按一下任何地方圖形而不需要避免裝飾項目。  
  
## 從命令處理常式來存取目前的選取範圍  
 定義域專屬語言的命令集類別包含您的自訂命令的命令處理常式。<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> ，定義域專屬語言的命令集類別衍生的類別，提供用於存取目前的選取範圍的幾位成員。  
  
 根據命令，命令處理常式可能需要在模型設計師、 模型總管\] 中或使用中視窗中的選取項目。  
  
#### 若要存取選取項目資訊  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 類別會定義下列可用來存取目前的選取範圍的成員。  
  
    |成員|描述|  
    |--------|--------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> 方法|傳回 `true` 是否有任何項目模型設計工具中選取區間圖形; 否則 `false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> 方法|傳回 `true` 圖表就會選取在模型設計師中，否則如果 `false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> 方法|傳回 `true` 如果只有一個項目就會選取在模型設計師中，否則 `false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> 方法|傳回 `true` 選取使用中視窗; 否則只有一個項目是否 `false`。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> 屬性|取得唯讀的集合，在模型設計師中選取的項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> 屬性|取得唯讀的集合，在使用中視窗中選取的項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> 屬性|取得在模型設計師中的選取範圍的主要項目。|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> 屬性|取得使用中視窗的選取範圍的主要項目。|  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> 屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 類別可提供存取 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> 物件，代表模型設計工具視窗，並在模型設計師中選取的項目提供額外的存取。  
  
3.  此外，產生的程式碼定義 explorer 工具視窗的屬性，並在命令中的檔案總管選取項目屬性設定為網域特定語言的類別。  
  
    -   Explorer 工具視窗的屬性會傳回定義域專屬語言總管工具視窗類別的執行個體。 Explorer 工具視窗類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> 類別，並代表模型總管\] 中的定義域專屬語言。  
  
    -   `ExplorerSelection` 屬性會傳回網域特定語言的模型總管\] 視窗中選取的項目。  
  
## 判斷哪一個視窗作用中  
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 介面包含定義可提供存取目前的選取狀態，在介面中的成員。 您可以取得 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 物件與套件類別或網域特定語言，透過命令集類別 `MonitorSelection` 每個基底類別中定義的屬性。 封裝類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> 類別，而且命令集類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 類別。  
  
#### 若要判斷命令處理常式從何種視窗是作用中  
  
1.  <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> 屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> 類別會傳回 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 可讓您存取命令介面中目前的選取項目狀態的物件。  
  
2.  <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> 屬性 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> 介面取得使用中的選取範圍的容器，可以不同於使用中視窗。  
  
3.  新增下列屬性以命令類別為您設定來判斷何種視窗是作用中的定義域專屬語言。  
  
    ```c#  
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
  
## 將選取範圍的限制  
 藉由新增選取規則，您可以控制使用者在模型中選取項目時，會選取哪些項目。 例如，若要允許使用者視為單一單位的項目數目，您可以使用選取規則。  
  
#### 若要建立選取範圍規則  
  
1.  在 DSL 專案中建立自訂程式碼檔案  
  
2.  定義衍生自選取規則類別 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> 類別。  
  
3.  覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> 選取規則類別來套用選取準則的方法。  
  
4.  將 ClassDiagram 類別的部分類別定義新增至您的自訂程式碼檔案。  
  
     `ClassDiagram` 類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> 類別，並在產生的程式碼檔案中，Diagram.cs，DSL 專案中定義。  
  
5.  覆寫 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 屬性 `ClassDiagram` 類別，以傳回自訂規則。  
  
     預設實作 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> 屬性取得選取範圍規則物件，不會修改選取範圍。  
  
### 範例  
 下列程式碼檔案會建立會包含每一開始所選取的網域圖形的所有執行個體選取範圍擴展的選取範圍規則。  
  
```c#  
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
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>