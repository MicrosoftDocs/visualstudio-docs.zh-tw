---
title: 使用 MEF 擴充您的 DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40442d9cf740bd4122aaf48f82fdba425aff261e
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415573"
---
# <a name="extend-your-dsl-by-using-mef"></a>使用 MEF 擴充您的 DSL

您可以使用 Managed Extensibility Framework (MEF) 來擴充您的特定領域語言 (DSL)。 您或其他開發人員能夠撰寫 dsl 的延伸模組，而不需要變更程式碼與 DSL 定義中。 這類延伸包括功能表命令、 拖放處理常式，以及驗證。 使用者將能夠安裝 DSL，然後再選擇性地，安裝延伸模組。

此外，當您啟用 MEF DSL 中，它可以是您更輕鬆地撰寫您的 DSL 的功能即使它們皆已內建與 DSL。

如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>若要啟用以 MEF 擴充您的 DSL

1.  建立新的資料夾，名為**MefExtension**內**DslPackage**專案。 將下列檔案新增至它：

     檔案名稱： `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > 設定在這個檔案是定義於 DslPackage\GeneratedCode\Constants.tt GUID CommandSetId 相同的 GUID

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    檔案名稱： `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    檔案名稱： `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    檔案名稱： `ValidationExtensionRegistrar.tt`

    如果您加入這個檔案，您必須啟用您的 DSL 的驗證使用中的交換器，至少一個**EditorValidation** DSL 總管 中。

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    檔案名稱： `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2.  建立新的資料夾，名為**MefExtension**內**Dsl**專案。 將下列檔案新增至它：

     檔案名稱： `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    檔案名稱： `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    檔案名稱： `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3.  將下行新增至現有的檔案，稱為**DslPackage\Commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    在現有插入一行`<Include>`指示詞。

4.  開啟*DslDefinition.dsl*。

5.  在 [DSL 總管] 中，選取**於**。

6.  在 [屬性] 視窗中，請確定至少一個屬性名為**會使用**是`true`。

7.  在 **方案總管**工具列上，按一下**轉換所有範本**。

     分公司的檔案會出現下方每個您新增的檔案。

8.  建置並執行解決方案，以驗證它仍然運作。

您的 DSL 現在是 MEF 啟用。 您可以將功能表命令、 軌跡處理常式和驗證條件約束撰寫成 MEF 擴充功能中。 您可以在您的 DSL 方案，以及其他自訂程式碼中撰寫這些擴充功能。 此外，您或其他開發人員可以撰寫擴充您的 DSL 的個別 Visual Studio 擴充功能。

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>建立已啟用 MEF 的 DSL 延伸模組

如果您有啟用 MEF 的 DSL，由自己還是他人的存取，您可以為它撰寫延伸模組。 擴充功能可用來加入功能表命令、 軌跡處理常式或驗證條件約束。 若要製作這些擴充功能，您可以使用 Visual Studio 擴充功能 (VSIX) 方案。 方案有兩個部分： 建置程式碼組件的類別庫專案和封裝組件的 VSIX 專案。

### <a name="to-create-a-dsl-extension-vsix"></a>若要建立的 DSL 延伸模組的 VSIX

1. 建立新**類別庫**專案。

2. 在新的專案中，加入 DSL 的組件的參考。

   - 這個組件通常具有名稱的結尾 」。Dsl.dll"。

   - 如果您有 DSL 專案的存取權，您可以找到組件檔案的目錄下**Dsl\bin\\\\***

   - 如果您的 DSL 的 VSIX 檔案存取，您可以將 VSIX 檔案的副檔名變更為 「.zip 」 來尋找組件。 將解壓縮的.zip 檔案。

3. 加入下列.NET 組件的參考：

   -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   -   System.ComponentModel.Composition.dll

   -   System.Windows.Forms.dll

4. 建立新**VSIX 專案**專案。

5. 在 **方案總管**，以滑鼠右鍵按一下 VSIX 專案，然後選擇**設定為啟始專案**。

6. 在新的專案中，開啟**source.extension.vsixmanifest**。

7. 按一下 **將內容加入**。 在對話方塊中，將**內容的型別**要**MEF 元件**，和**原始碼專案**您類別庫專案。

8. 加入至 DSL 的 VSIX 參考。

   1. 在  **source.extension.vsixmanifest**，按一下 **加入參考**

   2. 在對話方塊中，按一下**新增裝載**，然後尋找 DSL 的 VSIX 檔案。 在 VSIX 檔案建置在 DSL 方案中，* * DslPackage\bin\\\\* * *。

       這可讓使用者安裝 DSL 和擴充功能，在相同的時間。 如果使用者已經安裝 DSL，將會安裝您的擴充。

9. 檢閱及更新的其他欄位**source.extension.vsixmanifest**。 按一下 **選取版本**並確認已設定正確的 Visual Studio 版本。

10. 加入類別庫專案中的程式碼。 使用下一節的範例，做為指南。

     您可以新增任意數目的命令、 手勢和驗證類別。

11. 若要測試此擴充功能，請按**F5**。 在 Visual Studio 的實驗性執行個體，建立或開啟 DSL 的範例檔案。

## <a name="writing-mef-extensions-for-dsls"></a>撰寫 Dsl MEF 擴充功能

您可以撰寫延伸模組組件程式碼專案的另一個 DSL 延伸模組方案。 您也可以在 DslPackage 專案中，使用 MEF，是為了方便撰寫命令、 手勢和驗證程式碼做為 DSL 的一部分。

### <a name="menu-commands"></a>功能表命令

若要撰寫功能表命令，定義類別可實作<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>具有名為您的 DSL 中定義屬性類別做為前置詞*您的 Dsl*`CommandExtension`。 您可以撰寫一個以上的功能表命令類別。

`QueryStatus()` 每當使用者以滑鼠右鍵按一下圖表，就會呼叫。 它應該檢查目前的選取範圍，並設定`command.Enabled`表示命令時適用。

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>軌跡處理常式

軌跡處理常式可以處理拖曳至圖表，來源內的任何位置，或在 Visual Studio 外部的物件。 下列範例可讓使用者從 Windows 檔案總管將檔案拖曳到圖表上。 它會建立包含檔案名稱的項目。

您可以撰寫處理常式來處理來自其他 DSL 模型和 UML 模型拖曳的。 如需詳細資訊，請參閱[如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)。

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>驗證條件約束

驗證方法會標示`ValidationExtension`屬性所產生的 DSL 中，與也<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>。 此方法可以出現在屬性未標記的任何類別。

如需詳細資訊，請參閱 <<c0> [ 定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>另請參閱

- [推出 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)
