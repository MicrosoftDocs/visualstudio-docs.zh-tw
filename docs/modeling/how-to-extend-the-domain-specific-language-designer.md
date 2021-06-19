---
title: 如何：擴充網域指定的語言設計工具
description: 瞭解如何將擴充功能延伸至您用來編輯特定領域語言 (DSL) 定義的設計工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9354e3b846f48a79aa5cdd0f39a159bd007cdd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387213"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>如何：擴充網域指定的語言設計工具

您可以對用來編輯 DSL 定義的設計工具進行擴充。 您可以進行的延伸模組類型包括加入功能表命令、新增拖曳和按兩下手勢的處理常式，以及特定類型值或關聯性變更時所觸發的規則。 擴充功能可以封裝為 Visual Studio 整合延伸模組 (VSIX) 並散發給其他使用者。

如需此功能的範例程式碼和詳細資訊，請參閱 Visual Studio [視覺效果和模型 SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)。

## <a name="set-up-the-solution"></a>設定解決方案

設定包含擴充程式碼的專案，以及可匯出專案的 VSIX 專案。 您的方案可以包含併入相同 VSIX 的其他專案。

### <a name="to-create-a-dsl-designer-extension-solution"></a>建立 DSL 設計工具擴充方案

1. 使用 [ **類別庫** ] 專案範本建立新專案。 此專案將包含您的延伸模組程式碼。

2. 建立新的 **VSIX 專案** 專案。

     選取 [ **加入至方案**]。

     *Extension.vsixmanifest* 會在 VSIX 資訊清單編輯器中開啟。

3. 按一下 [內容] 欄位上方的 [ **新增內容**]。

4. 在 [ **加入內容** ] 對話方塊中，將 [ **選取內容類型** ] 設定為 [ **MEF 元件**]，並將 **專案** 設定為類別庫專案。

5. 按一下 [ **選取版本** ] 並確定已核取 **Visual Studio Enterprise** 。

6. 請確定 VSIX 專案是方案的啟始專案。

7. 在類別庫專案中，加入下列元件的參考：

     VisualStudio. CoreUtility

     VisualStudio （node.js）

     VisualStudio （node.js）。

     VisualStudio. Dsldefinition.dsl 檔. 11。0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>測試和部署

若要測試此主題中的任何延伸模組，請建立並執行方案。 Visual Studio 的實驗執行個體隨即開啟。 在此情況下，請開啟 DSL 解決方案。 編輯 Dsldefinition.dsl 檔圖。 您可以看到延伸模組行為。

若要將延伸模組部署到主要 Visual Studio 以及其他電腦，請遵循下列步驟：

1. 在 node.js 中的 vsix 專案中尋找 vsix 安裝檔案 \\ * \\ \*

2. 將此檔案複製到目的電腦，然後在 Windows 檔案總管 (或檔案總管) 中按兩下它。

     Visual Studio 的延伸模組管理員會開啟，確認已安裝擴充功能。

若要卸載擴充功能，請遵循下列步驟：

1. 在 Visual Studio 中，按一下 [ **工具** ] 功能表上的 [ **擴充管理員**]。

2. 選取擴充功能，並將其刪除。

## <a name="add-a-shortcut-menu-command"></a>新增快捷方式功能表命令

若要讓快捷方式功能表命令出現在 DSL 設計工具介面或 [DSL Explorer] 視窗中，請撰寫類似下列的類別。

類別必須執行 `ICommandExtension` ，而且必須有屬性 `DslDefinitionModelCommandExtension` 。

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>處理滑鼠手勢

此程式碼類似于功能表命令的程式碼。

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>回應值變更

此處理程式需要網域模型才能正確運作。 我們提供簡單的領域模型。

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

下列程式碼會實行簡單的模型。 建立新的 GUID 以取代預留位置。

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```