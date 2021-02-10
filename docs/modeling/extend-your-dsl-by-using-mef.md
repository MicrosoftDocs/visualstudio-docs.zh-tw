---
title: 使用 MEF 擴充您的 DSL
description: 瞭解如何使用 Managed Extensibility Framework (MEF) ，來擴充特定領域語言 (DSL) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 324037010e642ab4e96f6efea5da0f232c9bd530
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935062"
---
# <a name="extend-your-dsl-by-using-mef"></a>使用 MEF 擴充您的 DSL

您可以使用 Managed Extensibility Framework (MEF) ，將特定領域語言 (DSL) 擴充。 您或其他開發人員將能夠撰寫 DSL 的延伸模組，而不需要變更 DSL 定義和程式碼。 這類延伸模組包括功能表命令、拖放處理常式和驗證。 使用者將可以安裝您的 DSL，然後選擇性地安裝其擴充功能。

此外，當您在 DSL 中啟用 MEF 時，您可以更輕鬆地撰寫 DSL 的一些功能，即使它們全都與 DSL 一起建立也是一樣。

如需 MEF 的詳細資訊，請參閱 [Managed Extensibility Framework (mef) ](/dotnet/framework/mef/index)。

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>啟用 MEF 擴充您的 DSL

1. 在 **DslPackage** 專案內建立名為 **MefExtension** 的新資料夾。 在其中新增下列檔案：

     檔案名： `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > 將此檔案中的 GUID 設定為與 DslPackage\GeneratedCode\Constants.tt 中定義的 GUID CommandSetId 相同。

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

    檔案名： `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    檔案名： `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    檔案名： `ValidationExtensionRegistrar.tt`

    如果您新增此檔案，您必須在 dsl Explorer 中使用至少一個 **EditorValidation** 參數，在 dsl 中啟用驗證。

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    檔案名： `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. 在 **Dsl** 專案內建立名為 **MefExtension** 的新資料夾。 在其中新增下列檔案：

     檔案名： `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    檔案名： `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    檔案名： `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. 將下列程式程式碼新增至名為 **DslPackage\Commands.vsct** 的現有檔案：

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    在現有指示詞之後插入該行 `<Include>` 。

4. 開啟 *dsldefinition.dsl 檔。*

5. 在 [DSL Explorer] 中，選取 [ **Editor\Validation**]。

6. 在屬性視窗中，請確定至少有一個名為 [ **使用** ] 的屬性是 `true` 。

7. 在 [ **方案總管** ] 工具列中，按一下 [ **轉換所有範本**]。

     附屬檔案會顯示在您新增的每個檔案底下。

8. 建立並執行方案，以確認它仍在運作中。

您的 DSL 現在已啟用 MEF。 您可以撰寫功能表命令、手勢處理常式和驗證條件約束做為 MEF 延伸模組。 您可以將這些擴充功能與其他自訂程式碼一起寫入您的 DSL 解決方案中。 此外，您或其他開發人員可以撰寫擴充 DSL 的個別 Visual Studio 延伸模組。

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>建立已啟用 MEF 之 DSL 的延伸模組

如果您可以存取您自己或其他人所建立且已啟用 MEF 的 DSL，您可以為其撰寫延伸模組。 擴充功能可以用來加入功能表命令、手勢處理常式或驗證條件約束。 若要撰寫這些擴充功能，您可以使用 (VSIX) 解決方案的 Visual Studio 延伸模組。 解決方案有兩個部分：建立程式碼元件的類別庫專案，以及封裝元件的 VSIX 專案。

### <a name="to-create-a-dsl-extension-vsix"></a>建立 DSL 延伸模組 VSIX

1. 建立新的 **類別庫** 專案。

2. 在新專案中，加入 DSL 元件的參考。

   - 這個元件的名稱通常會以 ".Dsl.dll" 結尾。

   - 如果您有 DSL 專案的存取權，您可以在目錄 **DSL \\ bin \\ \*** 下找到元件檔案。

   - 如果您可以存取 DSL VSIX 檔案，您可以藉由將 VSIX 檔案的副檔名變更為 ".zip" 來尋找元件。 將 .zip 檔案解壓縮。

3. 新增下列 .NET 元件的參考：

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. 建立新的 **VSIX 專案** 專案。

5. 在 **方案總管** 中，以滑鼠右鍵按一下 VSIX 專案，然後選擇 [ **設定為啟始專案**]。

6. 在新的專案中，開啟 **extension.vsixmanifest**。

7. 按一下 [ **新增內容**]。 在對話方塊中，將 [ **內容類型** ] 設定為 [ **MEF 元件**]，並將 [ **來源專案** ] 設定為類別庫專案。

8. 將 VSIX 參考新增至 DSL。

   1. 在 **extension.vsixmanifest** 中，按一下 [**加入參考**]

   2. 在對話方塊中，按一下 [ **新增** 內容]，然後找出 DSL 的 VSIX 檔案。 VSIX 檔案內建于 DSL 解決方案的 **DslPackage \\ bin \\ \*** 中。

       這可讓使用者同時安裝 DSL 和您的延伸模組。 如果使用者已安裝 DSL，則只會安裝您的延伸模組。

9. 檢查並更新 **extension.vsixmanifest** 的其他欄位。 按一下 [ **選取版本** ]，並確認已設定正確的 Visual Studio 版本。

10. 將程式碼加入至類別庫專案。 使用下一節中的範例做為指南。

     您可以新增任意數目的命令、手勢和驗證類別。

11. 若要測試擴充功能，請按 **F5**。 在 Visual Studio 的實驗實例中，建立或開啟 DSL 的範例檔案。

## <a name="writing-mef-extensions-for-dsls"></a>撰寫適用于 Dsl 的 MEF 擴充功能

您可以在不同 DSL 擴充方案的元件程式碼專案中撰寫延伸模組。 您也可以在 DslPackage 專案中使用 MEF，這是一種方便的方式，可將命令、手勢和驗證程式代碼撰寫為 DSL 的一部分。

### <a name="menu-commands"></a>功能表命令

若要撰寫功能表命令，請 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> 使用您的 DSL 中定義的屬性（名稱為 *dsl*），來定義可執行和前置類別的類別 `CommandExtension` 。 您可以撰寫一個以上的功能表命令類別。

`QueryStatus()` 只要使用者以滑鼠右鍵按一下圖表，就會呼叫。 它應該會檢查目前的選取範圍，並設定 `command.Enabled` 來指出命令的適用時機。

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

軌跡處理常式可以處理從任何地方（Visual Studio 內部或外部）拖曳到圖表上的物件。 下列範例可讓使用者將檔案從 Windows 檔案總管拖曳至圖表上。 它會建立包含檔案名的元素。

您可以撰寫處理常式來處理來自其他 DSL 模型和 UML 模型的拖曳。 如需詳細資訊，請參閱 [如何：新增拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)。

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

驗證方法是由 DSL 所 `ValidationExtension` 產生的屬性標記，也會由所產生 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> 。 方法可以出現在未以屬性標記的任何類別中。

如需詳細資訊，請參閱 [以 Domain-Specific 語言進行驗證](../modeling/validation-in-a-domain-specific-language.md)。

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
- [如何：加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)
