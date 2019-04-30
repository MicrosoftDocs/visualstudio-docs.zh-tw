---
title: 將 UML 圖表匯出至影像檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: b29ce2a5-0ee3-4ab7-9aa3-13ca9c6b37a2
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c04b8bd4ab956fe60191237910db35e2e463d3e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442940"
---
# <a name="export-uml-diagrams-to-image-files"></a>將 UML 圖表匯出至影像檔案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以匯出 UML 文件從[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]到受程式控制的映像。 例如，您可能想要在文件自動產生程序進行時執行此作業。  
  
 如果您想要手動將文件匯出到影像，您可以複製圖表中的圖形並貼到其他程式，例如 Word。 您也可以將文件列印成 XPS 格式。 如需詳細資訊，請參閱 <<c0> [ 將圖表匯出為影像](../modeling/export-diagrams-as-images.md)。  
  
## <a name="saving-an-image"></a>儲存影像  
 下列程式碼會定義捷徑功能表命令 (也稱為內容功能表命令)，這些命令會將影像儲存到檔案。  
  
> [!NOTE]
> 若要將此程式碼做為功能表命令執行，您必須將它併入 MEF 元件。 如需詳細資訊，請參閱 <<c0> [ 在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
 程式碼會先使用 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape.GetObject%2A> 以取得基礎實作的 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>。 這個類型具有 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.CreateBitmap%2A> 方法。  
  
```  
namespace SaveToImage  
{  
  using System.ComponentModel.Composition; // for [Import], [Export]  
  using System.Drawing; // for Bitmap  
  using System.Drawing.Imaging; // for ImageFormat  
  using System.Linq; // for collection extensions  
  using System.Windows.Forms; // for SaveFileDialog  
  using Microsoft.VisualStudio.Modeling.Diagrams;  
    // for Diagram  
  using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
    // for IDiagramContext  
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    // for designer extension attributes  
  
  /// <summary>  
  /// Called when the user clicks the menu item.  
  /// </summary>  
  // Context menu command applicable to any UML diagram   
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  [UseCaseDesignerExtension]  
  [SequenceDesignerExtension]  
  [ComponentDesignerExtension]  
  [ActivityDesignerExtension]  
  class CommandExtension : ICommandExtension  
  {  
    [Import]  
    IDiagramContext Context { get; set; }  
  
    public void Execute(IMenuCommand command)  
    {  
      // Get the diagram of the underlying implementation.  
      Diagram dslDiagram = Context.CurrentDiagram.GetObject<Diagram>();  
      if (dslDiagram != null)  
      {  
        string imageFileName = FileNameFromUser();  
        if (!string.IsNullOrEmpty(imageFileName))  
        {  
          Bitmap bitmap = dslDiagram.CreateBitmap(  
           dslDiagram.NestedChildShapes,  
           Diagram.CreateBitmapPreference.FavorClarityOverSmallSize);  
          bitmap.Save(imageFileName, GetImageType(imageFileName));  
        }  
      }  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Set Enabled and Visible to specify the menu item status.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = Context.CurrentDiagram != null   
        && Context.CurrentDiagram.ChildShapes.Count() > 0;  
    }  
  
    /// <summary>  
    /// Menu text.  
    /// </summary>  
    public string Text  
    {  
      get { return "Save To Image..."; }  
    }  
  
    /// <summary>  
    /// Ask the user for the path of an image file.  
    /// </summary>  
    /// <returns>image file path, or null</returns>  
    private string FileNameFromUser()  
    {  
      SaveFileDialog dialog = new SaveFileDialog();  
      dialog.AddExtension = true;  
      dialog.DefaultExt = "image.bmp";  
      dialog.Filter = "Bitmap ( *.bmp )|*.bmp|JPEG File ( *.jpg )|*.jpg|Enhanced Metafile (*.emf )|*.emf|Portable Network Graphic ( *.png )|*.png";  
      dialog.FilterIndex = 1;  
      dialog.Title = "Save Diagram to Image";  
      return dialog.ShowDialog() == DialogResult.OK ? dialog.FileName : null;  
    }  
  
    /// <summary>  
    /// Return the appropriate image type for a file extension.  
    /// </summary>  
    /// <param name="fileName"></param>  
    /// <returns></returns>  
    private ImageFormat GetImageType(string fileName)  
    {  
      string extension = System.IO.Path.GetExtension(fileName).ToLowerInvariant();  
      ImageFormat result = ImageFormat.Bmp;  
      switch (extension)  
      {  
        case ".jpg":  
          result = ImageFormat.Jpeg;  
          break;  
        case ".emf":  
          result = ImageFormat.Emf;  
          break;  
        case ".png":  
          result = ImageFormat.Png;  
          break;  
      }  
      return result;  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [將圖表匯出為影像](../modeling/export-diagrams-as-images.md)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
