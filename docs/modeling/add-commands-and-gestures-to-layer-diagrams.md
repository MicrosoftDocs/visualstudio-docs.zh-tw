---
title: 將命令和軌跡新增至相依性圖表
description: 瞭解如何在 Visual Studio 的相依性圖表上定義右鍵功能表命令和軌跡處理常式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc91e2c160d2081db868daf8d8dbaeb041172297
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362219"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>將命令和軌跡新增至相依性圖表

您可以在 Visual Studio 的相依性圖表上，定義右鍵功能表命令和軌跡處理常式。 您可以將這些擴充功能封裝成 Visual Studio 整合擴充功能 (VSIX)，您可將這整合擴充功能散發給其他 Visual Studio 使用者。

您可以視需要在相同的 Visual Studio 專案中定義許多命令和軌跡處理常式。 您也可以將許多這類專案合併成單一 VSIX。 例如，您可以定義包含圖層命令的單一 VSIX，以及特定領域的語言。

> [!NOTE]
> 您也可以自訂架構驗證，其中使用者的原始程式碼會與相依性圖表進行比較。 您應該要在個別的 Visual Studio 專案中定義架構驗證。 您可以將它加入相同的 VSIX，就像其他擴充功能一樣。 如需詳細資訊，請參閱 [將自訂架構驗證加入至](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)相依性圖表。

## <a name="requirements"></a>規格需求

請參閱 [需求](../modeling/extend-layer-diagrams.md#requirements)。

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>在新的 VSIX 中定義命令或手勢

建立擴充功能最快速的方法是使用專案範本。 這樣做會將程式碼和 VSIX 資訊清單放入相同的專案中。

1. 建立新的 **圖層設計工具命令延伸** 模組或 **圖層設計工具手勢延伸** 模組專案。

   此範本隨即建立包含小型工作範例的專案。

2. 若要測試擴充功能，請按下 **Ctrl** + **F5** 或 **F5**。

    Visual Studio 的實驗實例隨即啟動。 在此情況下，請建立相依性圖表。 您的命令或軌跡擴充功能應該會在此圖表中運作。

3. 關閉此實驗執行個體並修改此範例程式碼。

4. 您可以將其他命令或軌跡處理常式加入相同的專案。 如需詳細資訊，請參閱下列其中一節：

    [定義功能表命令](#command)

    [定義軌跡處理常式](#gesture)

::: moniker range="vs-2017"

5. 若要在 Visual Studio 的主要實例或其他電腦上安裝此延伸模組，請在 *bin* 目錄中尋找 *.vsix* 檔案。 將它複製到您要安裝它的電腦上，然後按兩下該檔案。 若要卸載，請選擇 [**工具**] 功能表上的 [**擴充功能和更新**]。

::: moniker-end

::: moniker range=">=vs-2019"

5. 若要在 Visual Studio 的主要實例或其他電腦上安裝此延伸模組，請在 *bin* 目錄中尋找 *.vsix* 檔案。 將它複製到您要安裝它的電腦上，然後按兩下該檔案。 若要卸載，請選擇 [**延伸** 模組] 功能表上的 [**管理擴充** 功能]。

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>將命令或手勢新增至不同的 VSIX

如果您想要建立包含命令、圖層驗證程式和其他擴充功能的單一 VSIX，建議您應建立單一專案來定義此 VSIX，並且針對此處理常式建立個別專案。

1. 建立新的 **類別庫** 專案。 這個專案將會包含命令或軌跡處理常式類別。

   > [!NOTE]
   > 雖然您可以在單一類別庫中定義多個命令或軌跡處理常式類別，不過您應該在個別的類別庫中定義圖層驗證類別。

2. 在您的方案中加入或建立 VSIX 專案。 VSIX 專案包含名為 **extension.vsixmanifest** 的檔案。

3. 在 **方案總管** 中，以滑鼠右鍵按一下 VSIX 專案，然後選擇 [ **設定為啟始專案**]。

4. 在 **source.extension.vsixmanifest** 的 [資產] 底下，加入命令或軌跡處理常式專案做為 MEF 元件。

    1. 在 [資產] 索引標籤中，選擇 [新增] 。

    2. 在 [類型] 選取 [Microsoft.VisualStudio.MefComponent] 。

    3. 在 [來源] 選取 [目前方案中的專案]  ，然後選取命令或軌跡處理常式專案的名稱。

    4. 儲存檔案。

5. 返回命令或軌跡處理常式專案，並加入下列專案參考：

   |**參考**|**這可讓您執行**|
   |-|-|
   |Program Files\Microsoft Visual Studio [版本]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|建立和編輯圖層|
   |Microsoft.VisualStudio.Uml.Interfaces|建立和編輯圖層|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|修改圖表上的圖形|
   |System.ComponentModel.Composition|使用 Managed Extensibility Framework (MEF) 定義元件|
   |Microsoft.VisualStudio.Modeling.Sdk.[版本]|定義模型擴充功能|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[版本]|更新圖形和圖表|

6. 編輯 C# 類別庫專案中的類別檔案，以便包含擴充功能的程式碼。 如需詳細資訊，請參閱下列其中一節：

     [定義功能表命令](#command)

     [定義軌跡處理常式](#gesture)

7. 若要測試此功能，請按下 **Ctrl** + **F5** 或 **F5**。

   Visual Studio 的實驗執行個體隨即開啟。 在此實例中，建立或開啟相依性圖表。

8. 若要在 Visual Studio 的主要實例中或在另一部電腦上安裝 VSIX，請在 VSIX 專案的 **bin** 目錄中尋找 **.vsix** 檔案。 將它複製到您想要安裝 VSIX 的電腦。 在檔案總管中，按兩下 VSIX 檔案。

## <a name="defining-a-menu-command"></a><a name="command"></a> 定義功能表命令

您可以將其他功能表命令定義加入現有的軌跡或命令專案。 每個命令都由具有下列特性的類別加以定義：

- 此類別的宣告方式如下：

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- 此類別的命名空間和名稱並不重要。

- 實作 `ICommandExtension` 的方法如下：

  - `string Text {get;}` - 出現在此功能表中的標籤。

  - `void QueryStatus(IMenuCommand command)` - 當使用者以滑鼠右鍵按一下此圖表時會被呼叫，並且判斷是否應該針對使用者的目前選取範圍顯示並啟用此命令。

  - `void Execute(IMenuCommand command)` - 當使用者選取此命令時會被呼叫。

- 若要判斷目前選取範圍，您可以匯入 `IDiagramContext`：

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

若要加入新的命令，請建立包含下列範例的新程式碼檔案。 然後，測試並編輯此檔案。

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> 定義軌跡處理常式

當使用者將專案拖曳至相依性圖表，以及當使用者按兩下圖表中的任何位置時，軌跡處理常式就會回應。

對於現有的命令或軌跡處理常式 VSIX 專案，您可以加入定義軌跡處理常式的程式碼檔案：

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

請注意下列有關軌跡處理常式的重點：

- `IGestureExtension` 的成員如下：

     **OnDoubleClick** - 當使用者在圖表上的任何位置按兩下時受呼叫。

     **CanDragDrop** - 當使用者移動滑鼠，同時將項目拖曳至此圖表上時，會重複受到呼叫。 它必須快速運作。

     **OnDragDrop** - 當使用者將項目置放到此圖表上時受呼叫。

- 每個方法的第一個引數是 `IShape`，您可以從這裡取得此圖層項目。 例如：

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- 針對某些拖曳項目類型的處理常式早已受到定義。 例如，使用者可以將方案總管中的專案拖曳至相依性圖表。 您無法針對這些項目類型定義拖曳處理常式。 在這些情況下，不會叫用您的 `DragDrop` 方法。

## <a name="see-also"></a>請參閱

- [將自訂架構驗證新增至相依性圖表](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
