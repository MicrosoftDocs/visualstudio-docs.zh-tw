---
title: 使用 MEF 擴充您的 DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a54aca1e3732f366172abc0b4acea92cd28c6fae
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="extend-your-dsl-by-using-mef"></a>使用 MEF 擴充您的 DSL
您可以使用 Managed Extensibility Framework (MEF) 擴充您的特定領域語言 (DSL)。 您或其他開發人員能夠撰寫 dsl 的擴充功能，而不需要變更 DSL 定義和程式碼。 這類延伸包括功能表命令、 拖放的處理常式，以及驗證。 使用者可以安裝 DSL，然後再選擇性地為其安裝擴充功能。

 此外，當您啟用 MEF DSL 中時，可能很您更輕鬆地撰寫的某些功能的 DSL，即使它們所有內建連同 DSL。

 如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)。

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>若要啟用要由 MEF 擴充 DSL

1.  建立新的資料夾，名為**MefExtension**內**DslPackage**專案。 將下列檔案：

     檔案名稱： `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    >  將 GUID 設定此檔案中以 DslPackage\GeneratedCode\Constants.tt 中會定義 GUID CommandSetId 相同

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

     如果您將加入這個檔案，您必須啟用 DSL 的驗證使用中的交換器其中**EditorValidation** DSL 總管 中。

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

     檔案名稱： `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2.  建立新的資料夾，名為**MefExtension**內**Dsl**專案。 將下列檔案：

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

3.  名為現有檔案中加入下行**DslPackage\Commands.vsct**:

    ```
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

     插入行後方`<Include>`指示詞。

4.  `Open DslDefinition.dsl.`

5.  在 DSL 總管 中，選取  **Editor\Validation**。

6.  在 [屬性] 視窗中，請確定至少一個屬性名為**使用...** 是`true`。

7.  在 [方案總管] 工具列中按一下**轉換所有範本**。

     分公司的檔案會顯示下每個您所加入的檔案。

8.  建置並執行方案來驗證它仍然運作。

 DSL 現在是 MEF 啟用。 您可以撰寫功能表命令、 軌跡處理常式，以及驗證條件約束做為 MEF 擴充功能。 您可以連同其他自訂程式碼 DSL 方案中撰寫這些擴充功能。 此外，您或其他開發人員可以撰寫個別[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充 DSL 的擴充功能。

## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>建立擴充的 MEF 啟用 DSL
 如果您有自己或其他人所建立的 MEF 啟用 DSL 的存取，您可以為它撰寫擴充功能。 擴充功能可以用來加入功能表命令、 軌跡處理常式或驗證條件約束。 若要撰寫這些擴充功能，您使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能 (VSIX) 解決方案。 方案中有兩個部分： 建置程式碼組件的類別庫專案和封裝組件的 VSIX 專案。

#### <a name="to-create-a-dsl-extension-vsix"></a>若要建立 DSL 擴充功能 VSIX

1.  建立新的類別庫專案。 若要這樣做，請在**新專案**對話方塊中，選取**Visual Basic**或**Visual C#** ，然後選取 **類別庫**。

2.  在新的類別庫專案，加入 DSL 的組件的參考。

    -   這個組件通常具有的名稱，結尾是"。Dsl.dll"。

    -   如果您有 DSL 專案存取權，您可以找到組件檔的目錄下**Dsl\bin\\\***

    -   如果您具有存取權 DSL VSIX 檔案時，您可以藉由變更 VSIX 檔案的副檔名為".zip"找到組件。 將解壓縮的.zip 檔案。

3.  加入下列.NET 組件的參考：

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

    -   System.ComponentModel.Composition.dll

    -   System.Windows.Forms.dll

4.  同一方案中建立 VSIX 專案。 若要這樣做，請在**新專案**對話方塊方塊中，展開  **Visual Basic**或**Visual C#**，按一下 **擴充性**，然後選取  **VSIX 專案**。

5.  在方案總管 中，以滑鼠右鍵按一下 VSIX 專案，然後按一下 **設定為啟始專案**。

6.  在新的專案中，開啟**source.extension.vsixmanifest**。

7.  按一下**將內容加入**。 在對話方塊中，設定**內容類型**至**MEF 元件**，和**原始碼專案**您類別庫專案。

8.  加入 DSL VSIX 參考。

    1.  在**source.extension.vsixmanifest**，按一下 **加入參考**

    2.  在對話方塊中，按一下 **加入裝載**然後找出的 DSL VSIX 檔案。 在建置 DSL 方案，在 VSIX 檔案**DslPackage\bin\\\***。

         這可讓使用者在相同的時間安裝 DSL 和擴充功能。 如果使用者已安裝 DSL，將會安裝您的擴充。

9. 檢閱及更新的其他欄位**source.extension.vsixmanifest**。 按一下**選取版本**並確認正確[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本設定。

10. 類別庫專案中加入程式碼。 使用下一節的範例，做為指南。

     您可以加入任意數目的命令、 手勢和驗證類別。

11. 若要測試擴充功能，請按**F5**。 在實驗執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，建立或開啟檔案的 DSL 範例。

## <a name="writing-mef-extensions-for-dsls"></a>撰寫 Dsl MEF 擴充功能
 您可以在個別的 DSL 擴充功能方案的組件程式碼專案中撰寫擴充功能。 您也可以在 DslPackage 專案中，使用 MEF，作為簡便方式，將命令、 手勢和驗證程式碼做為 DSL 的一部分。

### <a name="menu-commands"></a>功能表命令
 若要撰寫功能表命令，定義一個類別，實作<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>和前置詞的類別與屬性定義於 DSL，名為*YourDsl*`CommandExtension`。 您可以撰寫一個以上的功能表命令類別。

 `QueryStatus()` 每當使用者以滑鼠右鍵按一下圖表會呼叫。 它應該檢查目前的選取範圍，並設定`command.Enabled`指出命令適用。

```
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
 軌跡處理常式可以處理的物件內部或外部，拖曳到圖表上從任何地方， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 下列範例可讓使用者從 Windows 檔案總管將檔案拖曳到圖表。 它會建立包含檔案名稱的項目。

 您可以撰寫處理常式來處理來自其他 DSL 模型及 UML 模型的拖曳。 如需詳細資訊，請參閱[如何： 加入拖放的處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)。

```

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
 驗證方法會標示`ValidationExtension`DSL 與也會產生屬性<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>。 方法可以出現在任何屬性未標記的類別。

 如需詳細資訊，請參閱[中特定領域語言驗證](../modeling/validation-in-a-domain-specific-language.md)。

```
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