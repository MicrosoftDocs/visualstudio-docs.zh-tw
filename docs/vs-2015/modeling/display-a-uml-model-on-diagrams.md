---
title: 在圖表上顯示 UML 模型 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd30d626d6500f7bf904350133ea33f2b2a25ac5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757305"
---
# <a name="display-a-uml-model-on-diagrams"></a>在圖表上顯示 UML 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 擴充功能的程式碼中，您可以控制模型項目在圖表上顯示的方式。 若要查看哪些 Visual Studio 版本支援 UML 模型，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 本主題內容：  
 -   [若要在圖表上顯示項目](#Display)  
  
-   [存取代表項目的圖形](#GetShapes)  
  
-   [移動和調整大小圖形](#Moving)  
  
-   [若要從圖表移除圖形](#Removing)  
  
-   [開啟及建立圖表](#Opening)  
  
-   [範例： 對齊圖形的命令](#AlignCommand)  
  
##  <a name="Display"></a> 若要在圖表上顯示項目  
 當您建立項目 (例如，使用案例或動作) 時，使用者可以在 [UML 模型總管] 中看見該項目，但是該項目不一定會自動出現在圖表中。 在某些情況下，您必須撰寫程式碼來顯示它。 下表摘要說明一些替代方式。  
  
|項目的類型|例如|若要顯示此內容，您的程式碼必須|  
|---------------------|-----------------|-------------------------------------|  
|分類器|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|在指定的圖表上建立相關聯的圖形。 您可以為每一個分類器建立任意數目的圖形。<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> 針對此圖表頂端的圖形，請將 `parentShape` 設為 `null`。<br /><br /> 在某一個圖形內顯示另一個圖形。<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **注意：** 如果您執行內的顯示器**ILinkedUndo**交易，此方法有時候不會傳回`IShape`。 但是會正確建立此圖形，並且可以使用 `IElement.Shapes().` 存取。|  
|分類器的子系|屬性、作業、<br /><br /> 組件、通訊埠|自動 - 不需要程式碼。<br /><br /> 它會做為父系的一部分顯示。|  
|行為|互動 (序列)、<br /><br /> 活動|將行為繫結至適當的圖表。<br /><br /> 每一個行為每次最多可以繫結至一個圖表。<br /><br /> 例如: <br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|行為的子系|生命線、訊息、動作、物件節點|自動 - 不需要程式碼。<br /><br /> 它會在此父系繫結至圖表時顯示。|  
|資料庫關聯圖|關聯、一般化、流程、相依性|自動 - 不需要程式碼。<br /><br /> 它會在兩端都顯示的每一個圖表上顯示。|  
  
##  <a name="GetShapes"></a> 存取代表項目的圖形  
 圖形，其代表項目屬於下列類型：  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 何處*ElementType*是一種模型項目，例如`IClass`或`IUseCase`。  
  
|||  
|-|-|  
|`anElement.Shapes ()`|在開啟的圖表中所有代表這個項目的 `IShapes`。|  
|`anElement.Shapes(aDiagram)`|在特定圖表上所有代表這個項目的 `IShapes`。|  
|`anIShape.GetElement()`|該圖形所代表的 `IElement`。 您通常會將其轉換成 IElement 的子類別。|  
|`anIShape.Diagram`|包含此圖形的 `IDiagram`。|  
|`anIShape.ParentShape`|包含 `anIShape` 的圖形。 例如，通訊埠圖形會包含在元件圖形內。|  
|`anIShape.ChildShapes`|`IShape` 或 `IDiagram` 內含的圖形。|  
|`anIShape.GetChildShapes<IUseCase>()`|`IShape` 或 `IDiagram` 內包含的圖形，代表指定類型的項目，例如 `IUseCase`。|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|將泛型 `IShape` 轉換成強類型 `IShape<IElement>`。|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|在參數化圖形類別之間轉換圖形。|  
  
##  <a name="Moving"></a> 移動和調整大小圖形  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|移動圖形或調整大小。|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|啟動此視窗並捲動該圖表，以便所有指定的圖形都能呈現。 這些圖形全都必須在此圖表上。 如果 `zoomToFit` 為 true，該圖表即會視需要縮放，使所有圖形都能呈現。|  
  
 如需範例，請參閱[定義對齊命令](#AlignCommand)。  
  
##  <a name="Removing"></a> 若要從圖表移除圖形  
 您可以刪除一些項目類型的圖形，而不需刪除該項目。  
  
|模型項目|若要移除圖形|  
|-------------------|-------------------------|  
|分類器：類別、介面、列舉、執行者、使用案例或元件|`shape.Delete();`|  
|行為：互動或活動|您可以從此專案中刪除該圖表。 請使用 `IDiagram.FileName` 取得此路徑。<br /><br /> 這樣做不會從模型刪除此行為。|  
|任何其他圖形|您無法從圖表明確刪除其他圖形。 如果從此模型中刪除該項目，或是從此圖表中移除父圖形，則此圖形將自動消失。|  
  
##  <a name="Opening"></a> 開啟及建立圖表  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>從命令或軌跡擴充功能存取使用者目前的圖表  
 在類別中宣告此匯入的屬性：  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 在方法中存取此圖表：  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
>  只有在您所處理的命令中，`IDiagram` 的執行個體 (及其子類型，例如 `IClassDiagram`) 才有效。 建議您不要將 `IDiagram` 物件保留在使用者重新取得控制權後仍會保存的變數中。  
  
 如需詳細資訊，請參閱 <<c0> [ 在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>取得開啟圖表的清單  
 此專案中目前開啟之圖表的清單：  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>存取專案中的圖表  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 應用程式開發介面可用以開啟及建立模型專案和圖表。  
  
 請注意從 `EnvDTE.ProjectItem` 到 `IDiagramContext` 的轉換。  
  
```  
  
      using EnvDTE; // Visual Studio API  
...  
[Import]  
public IServiceProvider ServiceProvider { get; set; }  
...  
// Get Visual Studio API  
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;  
// Get current Visual Studio project  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
// Open and process every diagram in the project.  
foreach (ProjectItem item in project.ProjectItems)  
{  
  // Cast ProjectItem to IDiagramContext  
  IDiagramContext context = item as IDiagramContext;  
  if (context == null)  
  {  
     // This is not a diagram file.  
     continue;  
  }  
  // Open the file and give the window the focus.  
  if (!item.IsOpen)  
  {  
      item.Open().Activate();  
  }  
  // Get the diagram.  
  IDiagram diagram = context.CurrentDiagram;  
  // Deal with specific diagram types.  
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;  
  if (seqDiagram != null)  
  { ... } } }  
```  
  
 在您將控制權傳回給 `IDiagram` 後， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的執行個體及其子類型即無效。  
  
 您也可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案取得模型存放區：  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
##  <a name="AlignCommand"></a> 範例： 對齊圖形的命令  
 下列程式碼實作工整對齊圖形的功能表命令。 使用者必須先以接近垂直或水平對齊的方式放置兩個以上的圖形。 然後此對齊命令可用來將圖形置中對齊。  
  
 若要讓此命令可供使用，請將此程式碼加入功能表命令專案，然後部署產生的擴充功能給您的使用者。 如需詳細資訊，請參閱 <<c0> [ 在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace AlignCommand  
{  
  // Implements a command to align shapes in a UML class diagram.  
  // The user first selects shapes that are roughly aligned either vertically or horizontally.  
  // This command will straighten them up.  
  
  // Place this file in a menu command extension project.  
  // See http://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See http://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See http://msdn.microsoft.com/library/ee330926.aspx  
    /// </summary>  
    [Import]  
    ILinkedUndoContext linkedUndo { get; set; }  
  
    /// <summary>  
    /// Called when the user selects the command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      Align(context.CurrentDiagram.SelectedShapes);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks on the diagram.  
    /// Determines whether the command is enabled.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;  
      // Make it visible if there are shapes selected:  
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);  
  
      // Make it enabled if there are two or more shapes that are roughly in line:  
      command.Enabled = currentSelection.Count() > 1  
        && (HorizontalAlignCenter(currentSelection) > 0.0  
        || VerticalAlignCenter(currentSelection) > 0.0);  
  
    }  
  
    /// <summary>  
    /// Title of the menu command.  
    /// </summary>  
    public string Text  
    {  
      get { return "Align Shapes"; }  
    }  
  
    /// <summary>  
    /// Find a horizontal line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double Y = -1.0;  
      double top = 0.0, bottom = shapes.First().Bottom();  
      foreach (IShape shape in shapes)  
      {  
        top = Math.Max(top, shape.Top());  
        bottom = Math.Min(bottom, shape.Bottom());  
      }  
      if (bottom > top) Y = (bottom + top) / 2.0;  
      return Y;  
    }  
  
    /// <summary>  
    /// Find a vertical line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double X = -1.0;  
      double left = 0.0, right = shapes.First().Right();  
      foreach (IShape shape in shapes)  
      {  
        left = Math.Max(left, shape.Left());  
        right = Math.Min(right, shape.Right());  
      }  
      if (right > left) X = (right + left) / 2.0;  
      return X;  
    }  
  
    /// <summary>  
    /// Line up those shapes that are roughly aligned.  
    /// </summary>  
    /// <param name="shapes"></param>  
    private void Align(IEnumerable<IShape> shapes)  
    {  
      if (shapes.Count() > 1)  
      {  
        // The shapes must all overlap either horizontally or vertically.  
        // Find a horizontal line that is covered by all the shapes:  
        double Y = HorizontalAlignCenter(shapes);  
        if (Y > 0.0) // Negative if they don't overlap.  
        {  
          // Adjust all the shape positions in one transaction:  
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
          {  
            foreach (IShape shape in shapes)  
            {  
              shape.AlignYCenter(Y);  
            }  
            t.Commit();  
          }  
        }  
        else  
        {  
          // Find a vertical line that is covered by all the shapes:  
          double X = VerticalAlignCenter(shapes);  
          if (X > 0.0) // Negative if they don't overlap.  
          {  
            // Adjust all the shape positions in one transaction:  
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
            {  
              foreach (IShape shape in shapes)  
              {  
                shape.AlignXCenter(X);  
              }  
              t.Commit();  
            }  
          }  
        }  
      }  
    }  
  }  
  
  /// <summary>  
  /// Convenience extensions for IShape.  
  /// </summary>  
  public static class IShapeExtension  
  {  
    public static double Bottom(this IShape shape)  
    {  
      return shape.YPosition + shape.Height;  
    }  
  
    public static double Top(this IShape shape)  
    {  
      return shape.YPosition;  
    }  
  
    public static double Left(this IShape shape)  
    {  
      return shape.XPosition;  
    }  
  
    public static double Right(this IShape shape)  
    {  
      return shape.XPosition + shape.Width;  
    }  
  
    public static void AlignYCenter(this IShape shape, double Y)  
    {  
      shape.Move(shape.XPosition, Y - shape.YCenter());  
    }  
  
    public static void AlignXCenter(this IShape shape, double X)  
    {  
      shape.Move(X - shape.XCenter(), shape.YPosition);  
    }  
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double YCenter(this IShape shape)  
    {  
        return shape.Height / 2.0;  
    }   
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double XCenter(this IShape shape)  
    {  
        return shape.Width / 2.0;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [巡覽 UML 模型](../modeling/navigate-the-uml-model.md)   
 [範例： 在圖表功能表命令上對齊圖形](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [範例： 建立項目、 圖形和造型](http://go.microsoft.com/fwlink/?LinkId=213811)



