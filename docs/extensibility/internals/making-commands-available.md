---
title: 提供可用命令 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14998b8dca3c14bdae4f00f1940c19b696646ff
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231853"
---
# <a name="making-commands-available"></a>提供命令使用

當多個 Vspackage 加入至 Visual Studio 時，使用者介面 (UI) 可能會變得過擁擠，使用命令。 您可以設計您的套件，以協助減少此問題，如下：

- 程式封裝，讓它在使用者時才會載入需要它。

- 程式封裝，使其命令才會顯示它們可能需要整合式的開發環境 (IDE) 的目前狀態的內容中。

## <a name="delayed-loading"></a>延遲載入

若要啟用的一般方式延遲載入是設計的 VSPackage，讓其命令會顯示在 UI 中，但直到使用者按一下其中一個命令，將不載入封裝本身。 若要這麼做，在.vsct 檔案中，建立不有任何命令旗標的命令。

下列範例顯示從.vsct 檔案功能表命令的定義。 這是 Visual Studio Package 範本所產生的命令時**功能表命令**選取範本中的選項。

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

在範例中，如果父群組中， `MyMenuGroup`，例如是最上層功能表的子系**工具** 功能表中，此命令將會看到該功能表上，但執行命令的封裝，將不會載入，直到按下命令由使用者。 不過，透過程式設計來實作命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，您可以啟用要先展開功能表，其中包含命令時載入的封裝。

請注意，延遲的載入可能也會改善啟動效能。

## <a name="current-context-and-the-visibility-of-commands"></a>目前的內容和可見性的命令

您可以程式設計 VSPackage 的命令要顯示或隱藏的取決於 VSPackage 資料的動作或目前相關的目前狀態。 您可以使用來設定它的命令的狀態通常實作 VSPackage<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法從<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，但這需要才能夠執行程式碼要載入 VSPackage。 相反地，我們建議您讓 IDE 管理命令的可見性，而不載入封裝。 若要這樣做，在.vsct 檔案中，關聯一或多個特殊的 UI 內容中的命令。 這些 UI 內容會由稱為 GUID 來識別*命令內容 GUID*。

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 監視所產生的使用者動作，例如載入專案，或將編輯建置變更。 發生變更時，會自動修改 IDE 的外觀。 下表顯示四個主要的內容，IDE 的變更，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]監視。

| 內容的型別 | 描述 |
|-------------------------| - |
| 作用中的專案類型 | 對於大部分的專案類型，這`GUID`值等同於 VSPackage 實作專案的 GUID。 不過，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案中使用 專案類型`GUID`做為值。 |
| 使用中視窗 | 一般而言，這是在建立索引鍵繫結的目前 UI 內容的最後一個主動式文件視窗。 不過，它也可能是一個工具視窗，類似於內部網頁瀏覽器的索引鍵繫結資料表。 多個索引標籤的文件視窗，例如 HTML 編輯器，為每個索引標籤會有不同的命令內容`GUID`。 |
| 作用中的語言服務 | 目前顯示在文字編輯器中的檔案與相關聯的語言服務。 |
| 作用中的工具視窗 | 工具視窗已開啟，並具有焦點。 |

第五個的主要內容區域是 IDE 的 UI 狀態。 UI 內容均由作用中的命令內容`GUID`s，如下所示：

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

這些 Guid 會標示為作用中或非使用中，根據 IDE 的目前狀態。 多個 UI 內容可同時處於作用中。

### <a name="hide-and-display-commands-based-on-context"></a>隱藏與顯示內容為基礎的命令

您可以顯示或隱藏在 IDE 中的 [套件] 命令，而不載入封裝本身。 若要這樣做，請定義命令封裝.vsct 檔案中使用`DefaultDisabled`， `DefaultInvisible`，並`DynamicVisibility`命令旗標並新增一或多個[VisibilityItem](../../extensibility/visibilityitem-element.md)項目[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)一節。 當指定的命令內容`GUID`會變成作用中，此命令會顯示不含載入封裝。

### <a name="custom-context-guids"></a>自訂內容的 Guid

如果未定義的 GUID 不適當的命令內容中，您可以定義在 VSPackage 中，並再進行程式設計，讓它成為作用中或非使用中，視需要控制命令的可見性。 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務：

- 註冊內容的 Guid (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法)。

- 取得內容的狀態`GUID`(藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法)。

- 開啟內容`GUID`s 開啟和關閉 (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法)。

    > [!CAUTION]
    > 請確定，VSPackage 不會影響任何現有內容 GUID 的狀態因為其他 Vspackage 可能取決於它們。

## <a name="example"></a>範例

VSPackage 命令的下列範例會示範動態可視性由命令內容管理，而不必載入 VSPackage 的命令。

命令是設定為啟用，而且顯示時的解決方案存在;也就是說，只要其中一個下列的命令內容的 Guid 是作用中：

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

在範例中，請注意，每個命令旗標是個別[命令旗標](../../extensibility/command-flag-element.md)項目。

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

也請注意，必須在個別指定每個 UI 內容`VisibilityItem`項目，如下所示。

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>另請參閱

- [將命令加入至 [方案總管] 工具列](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [MenuCommand 對比OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)
- [以動態方式加入功能表項目](../../extensibility/dynamically-adding-menu-items.md)
