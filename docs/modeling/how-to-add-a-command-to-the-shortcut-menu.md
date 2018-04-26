---
title: 如何：在捷徑功能表中加入命令
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6f3c17a388aa974b78fdecc108891cf3be17c0da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>如何：在捷徑功能表中加入命令
您可以將功能表命令加入網域指定的語言 (DSL)，以便您的使用者可以執行專屬 DSL 的工作。 當使用者以滑鼠右鍵按一下圖表時，命令會出現在內容 (捷徑) 功能表上。 您可以定義命令，使它只在特定的情況下出現在功能表中。 例如，您可以使命令只在使用者按一下特定類型的項目或處於特定狀態的項目時才可見。

 總結而言，這些步驟在 DslPackage 專案中執行，步驟如下所示：

1.  [宣告中 Commands.vsct 命令](#VSCT)

2.  [更新封裝的版本號碼中 Package.tt](#version)。 每當變更 Commands.vsct 時都必須這麼做

3.  [CommandSet 類別中撰寫方法](#CommandSet)要顯示的命令，以及定義您想要執行的命令。

 如需範例，請參閱[Visualization and Modeling SDK 網站](http://go.microsoft.com/fwlink/?LinkID=185579)。

> [!NOTE]
>  您也可以覆寫 CommandSet.cs 中的方法，即可修改部分現有命令 (例如剪下、貼上、全選和列印) 的行為。 如需詳細資訊，請參閱[如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

## <a name="defining-a-command-using-mef"></a>使用 MEF 定義命令
 Managed Extension Framework (MEF) 提供在圖表功能表上定義功能表命令的替代方法。 它的主要用途是讓您或其他方可以擴充 DSL。 使用者可以選擇僅安裝 DSL，也可以安裝 DSL 和擴充功能。 然而，在 DSL 上啟用 MEF 的初始工作之後，MEF 也會減少定義捷徑功能表命令的工作。

 在下列情況下，請使用本主題中的方法：

1.  您想要在功能表上定義功能表命令，而不是以滑鼠右鍵按一下捷徑功能表。

2.  您想要在功能表中定義特定的命令群組。

3.  您不要讓他人以自己的命令擴充 DSL。

4.  您只要定義一個命令。

 否則，請考慮使用 MEF 方法來定義命令。 如需詳細資訊，請參閱[使用 MEF 擴充 DSL](../modeling/extend-your-dsl-by-using-mef.md)。

##  <a name="VSCT"></a> 宣告中 Commands.Vsct 命令
 功能表命令在 DslPackage\Commands.vsct 中宣告。 這些定義指定功能表項目的標籤以及它們在功能表上的顯示位置。

 從數個位於目錄中的.h 檔案的檔案進行編輯，Commands.vsct，匯入的定義*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc。它還包括從 DSL 定義產生的 GeneratedVsct.vsct。

 如需.vsct 檔案的詳細資訊，請參閱[Visual Studio 命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

#### <a name="to-add-the-command"></a>加入命令

1.  在**方案總管 中**下**DslPackage**專案中，開啟 Commands.vsct。

2.  在 `Commands` 項目中，定義一或多個按鈕和群組。 A*按鈕*是功能表上的項目。 A*群組*為功能表中的區段。 若要定義這些項目，請加入下列項目：

    ```
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    >  每一個按鈕或群組都是以 GUID 和整數 ID 識別。 您可以使用相同的 GUID 建立數個群組和按鈕。 不過，它們必須具有不同的 ID。 GUID 的名稱與識別碼名稱會轉譯為實際的 Guid 和中的數字 Id`<Symbols>`節點。

3.  為命令加入可見度限制，令其只在網域指定的語言之內容中載入。 如需詳細資訊，請參閱[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)。

     若要這麼做，請在 `CommandTable` 項目之後的 `Commands` 項目中加入下列項目。

    ```
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4.  定義用於 GUID 和 ID 的名稱。 若要這麼做，請在 `Symbols` 項目之後的 `CommandTable` 項目中加入 `Commands` 項目。

    ```
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5.  將 `{000...000}` 取代為識別您群組和功能表項目的 GUID。 若要取得新的 GUID，請使用**建立 GUID**工具**工具**功能表。

    > [!NOTE]
    >  如果您加入更多群組或功能表項目，您就可以使用相同的 GUID。 不過，您必須為 `IDSymbols` 使用新的值。

6.  在您從此程序複製的程式碼中，將每個出現的下列字串取代為您自己的字串：

    -   `grpidMyMenuGroup`

    -   `cmdidMyContextMenuCommand`

    -   `guidCustomMenuCmdSet`

    -   `My Context Menu Command`

##  <a name="version"></a> 更新封裝中的版本 Package.tt
 每當您加入或變更命令時，請先更新套用到套件類別的 `version` 之 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 參數，然後再發行網域指定語言的新版本。

 由於套件類別定義於產生的檔案，因此請更新文字範本檔案中產生 Package.cs 檔的屬性。

#### <a name="to-update-the-packagett-file"></a>更新 Package.tt 檔

1.  在**方案總管 中**，請在**DslPackage**專案，在**GeneratedCode**資料夾中，開啟 Package.tt 檔案。

2.  找出 `ProvideMenuResource` 屬性。

3.  遞增屬性的 `version` 參數，這是第二個參數。 您可以依需要明確撰寫參數名稱以提醒您其用途。 例如: 

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

##  <a name="CommandSet"></a> 定義命令行為
 您的 DSL 已經有一些命令，這些命令實作於 DslPackage\GeneratedCode\CommandSet.cs 中宣告的部分類別。 若要加入新的命令，您必須建立含有相同類別之部分宣告的新檔案，以擴充此類別。 類別的名稱通常是 *\<YourDslName >*`CommandSet`。 以驗證類別的名稱並檢查其內容開頭非常有用。

 命令集類別衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>。

#### <a name="to-extend-the-commandset-class"></a>擴充 CommandSet 類別

1.  在 [方案總管] 的 DslPackage 專案中，開啟 [GeneratedCode] 資料夾，然後查看 CommandSet.tt 下方並開啟其產生的檔案 CommandSet.cs。 記下檔案中定義的命名空間和第一個類別的名稱。 例如，您可能會看到：

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  在**DslPackage**，建立名為的資料夾**自訂程式碼**。 在這個資料夾中，建立新的類別檔案命名為`CommandSet.cs`。

3.  在新檔案中，撰寫具有與產生部分類別相同之命名空間和名稱的部分宣告。 例如: 

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **請注意**如果您使用類別範本來建立新的檔案時，您必須更正命名空間和類別名稱。

### <a name="extend-the-command-set-class"></a>擴充命令集類別
 您的命令集程式碼通常需要匯入下列命名空間：

```
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 調整命名空間和類別名稱，以符合產生的 CommandSet.cs 中的命名空間和類別名稱：

```
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 您必須定義兩個方法，一個用來決定內容功能表上何時會顯示命令，另一個用來執行命令。 這些方法不是覆寫；您須另行在命令清單中註冊方法。

### <a name="define-when-the-command-will-be-visible"></a>定義命令何時可見
 對每一個命令定義 `OnStatus...` 方法，決定命令是否將出現在功能表上，以及它是否將被啟用或呈現為灰色。設定 `Visible` 的 `Enabled` 和 `MenuCommand` 屬性，如下列範例所示。 呼叫此方法是為了在每次使用者以滑鼠右鍵按一下圖表時都建構捷徑功能表，因此它必須快速運作。

 在本範例中，只有在使用者選取特定類型的圖形時才可見到命令，且只在至少其中一個所選項目處於特定狀態時才會啟用命令。 此範例是根據「類別圖 DSL」範本，而 ClassShape 和 ModelClass 是在 DSL 中所定義的類型：

```
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

 以下片段在 OnStatus 方法中通常很有用：

-   `this.CurrentSelection`. 此清單中一律包含使用者以滑鼠右鍵按一下的圖形。 如果使用者按一下圖表的空白部分，圖表會成為清單的唯一成員。

-   `this.IsDiagramSelected()` - `true` 如果使用者按一下圖表的空白部分。

-   `this.IsCurrentDiagramEmpty()`

-   `this.IsSingleSelection()` - 使用者未選取多個物件

-   `this.SingleSelection` - 使用者以滑鼠右鍵按一下的圖形或圖表

-   `shape.ModelElement as MyLanguageElement` - 以圖形表示的模型項目。

 如同一般方針，使 `Visible` 屬性相依於選取的項目，並使 `Enabled` 屬性相依於所選項目的狀態。

 OnStatus 方法不應變更市集的狀態。

### <a name="define-what-the-command-does"></a>定義命令執行的動作
 對每一個命令定義 `OnMenu...` 方法，執行使用者按一下功能表命令時的必要動作。

 如果您變更模型項目，您必須在異動內進行。 如需詳細資訊，請參閱[如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

 在本範例中，`ClassShape`、`ModelClass` 和 `Comment` 是在 DSL (衍生自「類別圖 DSL」範本) 中所定義的類型。

```
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 如需有關如何在模型中，瀏覽物件物件，以及有關如何建立物件和連結的詳細資訊，請參閱[如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

### <a name="register-the-command"></a>註冊命令
 在 C# 中重複執行您在 CommandSet.vsct 的 Symbols 區段中所做的 GUID 和 ID 值宣告：

```
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 使用相同的 GUID 值，當您插入**Commands.vsct**。

> [!NOTE]
>  如果您變更 VSCT 檔的 Symbols 區段，您必須也將這些宣告變更為相符。 您也應在 Package.tt 中遞增版本號碼

 將功能表命令註冊為此命令集的一部分。 圖表初始化時會呼叫 `GetMenuCommands()` 一次：

```
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>測試命令
 在 Visual Studio 的實驗執行個體中建置和執行 DSL。 在您指定的情況下，命令應會出現在捷徑功能表中。

#### <a name="to-exercise-the-command"></a>執行命令

1.  在**方案總管] 中**工具列上，按一下 [**轉換所有範本**。

2.  按**F5**重建方案，並開始偵錯的實驗組建的特定領域語言。

3.  在實驗組建中，開啟範例圖表。

4.  以滑鼠右鍵按一下圖表中的各種項目，以驗證命令是否已正確啟用或停用，以及是否適當顯示或隱藏，視選取的項目而定。

## <a name="troubleshooting"></a>疑難排解
 **命令不會出現在功能表：**

-   命令只會出現在 Visual Studio 的偵錯執行個體中，直到安裝 DSL 套件為止。 如需詳細資訊，請參閱[部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)。

-   請確定實驗範例具有此 DSL 的正確副檔名。 若要檢查副檔名，請在 Visual Studio 的主要執行個體中開啟 DslDefinition.dsl。 然後在 DSL Explorer 中，以滑鼠右鍵按一下 [編輯器] 節點，然後按一下 [屬性]。 在 [屬性] 視窗中，檢查 FileExtension 屬性。

-   您[遞增套件版本號碼](#version)嗎？

-   在 OnStatus 方法的開頭設定中斷點。 在圖表的任何部分上按一下滑鼠右鍵時，它應該會中斷。

     **不會呼叫 OnStatus 方法**:

    -   請確定您的 CommandSet 程式碼中的 GUID 和 ID 符合 Commands.vsct 的 Symbols 區段中的 GUID 和 ID。

    -   在 Commands.vsct 中，確定每個父節點中的 GUID 和 ID 識別正確的父群組。

    -   在 Visual Studio 命令提示字元中，輸入 devenv /rootsuffix exp /setup。 然後重新啟動 Visual Studio 的偵錯執行個體。

-   逐步執行 OnStatus 方法，以確認 command.Visible 和 command.Enabled 設為 true。

 **命令會出現在錯誤的位置或錯誤的功能表文字就會出現，**:

-   請確定 GUID 和 ID 的組合對此命令是唯一的。

-   確定已解除安裝舊版套件。

## <a name="see-also"></a>另請參閱

- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [如何： 修改標準功能表命令](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [部署特定領域語言方案](../modeling/deploying-domain-specific-language-solutions.md)
- [範例程式碼： 循環圖表](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]