---
title: 在 DSL 中修改標準功能表命令
description: 瞭解如何修改您的 DSL 中自動定義之一些標準命令的行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8b44631971db277adcb0292f43a8592775fb3a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922689"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>如何：使用網域指定的語言修改標準功能表命令

您可以針對 DSL 中自動定義的一些標準命令，修改其行為。 例如，您可以修改 **剪** 下，使其排除機密資訊。 若要執行這項操作，您可以覆寫命令集類別中的方法。 這些類別是在 DslPackage 專案的 CommandSet.cs 檔中定義，並且衍生自 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>。

> [!NOTE]
> 如果您想要建立自己的功能表命令，請參閱 [如何：將命令新增至快捷方式功能表](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)。

## <a name="what-commands-can-you-modify"></a>您可以修改哪些命令？

### <a name="to-discover-what-commands-you-can-modify"></a>找出您可以修改的命令

1. 在 `DslPackage` 專案中，開啟 `GeneratedCode\CommandSet.cs`。 您可以在方案總管中找到這個 c # 檔案作為的子公司 `CommandSet.tt` 。

2. 在這個檔案中尋找名稱結尾為 " `CommandSet` " 的類別，例如 `Language1CommandSet` 和 `Language1ClipboardCommandSet` 。

3. 在每個命令集類別中，輸入 "`override`"，後面接著一個空格。 IntelliSense 會顯示您可以覆寫的方法清單。 每個命令都有名稱開頭為 "`ProcessOnStatus`" 和 "`ProcessOnMenu`" 的一組方法。

4. 記下包含所要修改之命令的命令集類別。

5. 關閉檔案而不儲存您的編輯。

    > [!NOTE]
    > 您通常不應該編輯產生的檔案。 任何編輯在下次產生檔案時都會遺失。

## <a name="extend-the-appropriate-command-set-class"></a>擴充適當的命令集類別

建立包含命令集類別之部分宣告的新檔案。

### <a name="to-extend-the-command-set-class"></a>擴充命令集類別

1. 在 [方案總管] 的 DslPackage 專案中，開啟 [GeneratedCode] 資料夾，然後查看 CommandSet.tt 下方並開啟其產生的檔案 CommandSet.cs。 記下檔案中定義的命名空間和第一個類別的名稱。 例如，您可能會看到：

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. 在 **DslPackage** 中，建立名為 **自訂程式碼** 的資料夾。 在此資料夾中，建立名為的新類別檔案 `CommandSet.cs` 。

3. 在新檔案中，撰寫具有與產生部分類別相同之命名空間和名稱的部分宣告。 例如：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > 如果您使用類別檔案範本來建立新的檔案，您必須更正命名空間和類別名稱。

## <a name="override-the-command-methods"></a>覆寫命令方法

大部分的命令都有兩個相關聯的方法：名稱 `ProcessOnStatus` 如下的方法：決定是否應該顯示並啟用此命令。 這個方法會在使用者以滑鼠右鍵按一下圖表時呼叫，應該會快速執行並且不進行任何變更。 `ProcessOnMenu`...當使用者按一下命令時呼叫，並應該執行命令的功能。 您可能想覆寫其中一個或兩個方法。

### <a name="to-change-when-the-command-appears-on-a-menu"></a>變更命令何時顯示在功能表上

覆寫 ProcessOnStatus .。。方法。 這個方法應該設定其參數 MenuCommand 的 Visible 和 Enabled 屬性。 命令通常會檢視 this.CurrentSelection 以判斷是否會套用至所選項目，也可能檢視其屬性以判斷是否可在其目前的狀態中套用命令。

一般而言，Visible 屬性應取決於選取的項目。 決定命令在功能表上顯示為黑色或灰色的 Enabled 屬性，則應取決於所選項目的目前狀態。

下列範例會在使用者選取多個圖形時，停用 [刪除] 功能表項目。

> [!NOTE]
> 這個方法不會影響是否可透過按鍵來使用命令。 例如，停用 [刪除] 功能表項目無法防止透過 Delete 鍵叫用此命令。

```csharp
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

您最好先呼叫基底方法，處理所有不重要的類別和設定。

ProcessOnStatus 方法不應該在存放區中建立、刪除或更新項目。

### <a name="to-change-the-behavior-of-the-command"></a>變更命令的行為

覆寫 ProcessOnMenu .。。方法。 下列範例禁止使用者一次刪除多個項目，即使使用 Delete 鍵也不可以。

```csharp
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

如果您的程式碼變更存放區 (例如建立、刪除或更新項目或連結)，您必須在異動內進行。 如需詳細資訊，請參閱 [如何建立和更新模型元素](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)。

### <a name="write-the-code-of-the-methods"></a>撰寫方法的程式碼

下列程式碼片段在這些方法中通常很有用：

- `this.CurrentSelection`. 使用者以滑鼠右鍵按一下的圖形，一律會包含在此圖形和連接線清單中。 如果使用者按一下圖表的空白部分，圖表會成為清單的唯一成員。

- `this.IsDiagramSelected()` - `true` 如果使用者按一下圖表的空白部分。

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` -使用者未選取多個圖形

- `this.SingleSelection` -使用者以滑鼠右鍵按一下的圖形或圖表

- `shape.ModelElement as MyLanguageElement` -以圖形表示的模型元素。

如需如何從專案流覽至專案，以及如何建立物件和連結的詳細資訊，請參閱 [在程式碼中流覽和更新模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.Design.MenuCommand>
- [撰寫程式碼來自訂特定領域語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [如何：在捷徑功能表中加入命令](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [VSPackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 結構描述參考](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK-電路圖範例。廣泛的 DSL 自訂](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
