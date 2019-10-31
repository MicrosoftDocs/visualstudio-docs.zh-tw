---
title: 讓命令可供使用 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d30d71290c08019acfdc75313516d8b1b1c4be3a
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186354"
---
# <a name="making-commands-available"></a>讓命令可供使用

將多個 Vspackage 新增至 Visual Studio 時，使用者介面（UI）可能會與命令 overcrowded。 您可以程式設計套件以協助減少此問題，如下所示：

- 將套件程式設計成隻有在使用者需要它時才會載入。

- 將套件程式設計成隻有在整合式開發環境（IDE）目前狀態的內容中可能需要時，才會顯示其命令。

## <a name="delayed-loading"></a>延遲載入

啟用延遲載入的典型方式是設計 VSPackage，讓其命令顯示在 UI 中，但在使用者按一下其中一個命令之前，不會載入封裝本身。 若要完成這項操作，請在 .vsct 檔案中建立沒有命令旗標的命令。

下列範例顯示 .vsct 檔案中的功能表命令定義。 這是在選取範本中的**功能表命令**選項時，由 Visual Studio 封裝範本所產生的命令。

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

在範例中，如果父群組 `MyMenuGroup`是最上層功能表（例如 [**工具**] 功能表）的子系，則該命令會顯示在該功能表上，但在使用者按一下該命令之前，將不會載入執行命令的封裝。 不過，藉由程式設計命令以執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，您可以在第一次展開包含命令的功能表時，啟用封裝的載入。

請注意，延遲載入可能也會改善啟動效能。

## <a name="current-context-and-the-visibility-of-commands"></a>命令的目前內容和可見度

視 VSPackage 資料的目前狀態或目前相關的動作而定，您可以將 VSPackage 命令程式設計為可見或隱藏。 您可以讓 VSPackage 設定其命令的狀態，通常是從 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面使用 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> 方法的執行，但這需要先載入 VSPackage，然後才能執行程式碼。 相反地，我們建議您啟用 IDE 來管理命令的可見度，而不需要載入封裝。 若要這麼做，請在 .vsct 檔案中，將命令與一或多個特殊 UI 內容產生關聯。 這些 UI 內容是由稱為*命令內容 guid*的 GUID 所識別。

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會監視因使用者動作而產生的變更，例如載入專案或從編輯到建立。 當發生變更時，會自動修改 IDE 的外觀。 下表顯示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 監視器之 IDE 變更的四個主要內容。

| 內容類型 | 描述 |
|-------------------------| - |
| 作用中的專案類型 | 對於大部分的專案類型而言，這個 `GUID` 值與用來執行專案之 VSPackage 的 GUID 相同。 不過，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案會使用專案類型 `GUID` 做為值。 |
| 使用中視窗 | 一般而言，這是最後一個使用中的文件視窗，它會建立索引鍵系結的目前 UI 內容。 不過，它也可能是具有類似于內部網頁瀏覽器之按鍵系結表的工具視窗。 針對多索引標籤式文件視窗（例如 HTML 編輯器），每個索引標籤都有不同的命令內容 `GUID`。 |
| 主動式語言服務 | 與目前在文字編輯器中顯示之檔案相關聯的語言服務。 |
| 活動工具視窗 | 開啟並具有焦點的工具視窗。 |

第五個主要內容區域是 IDE 的 UI 狀態。 UI 內容是由 active 命令內容 `GUID`s 所識別，如下所示：

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

這些 Guid 會標示為作用中或非作用中，視 IDE 的目前狀態而定。 可以同時使用多個 UI 內容。

### <a name="hide-and-display-commands-based-on-context"></a>根據內容隱藏和顯示命令

您可以在 IDE 中顯示或隱藏封裝命令，而不需要載入封裝本身。 若要這麼做，請使用 `DefaultDisabled`、`DefaultInvisible`和 `DynamicVisibility` 命令旗標，並將一或多個[VisibilityItem](../../extensibility/visibilityitem-element.md)專案新增至[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)區段，以在封裝的 .vsct 檔案中定義命令。 當指定的命令內容 `GUID` 變成作用中狀態時，就會顯示命令，而不會載入封裝。

### <a name="custom-context-guids"></a>自訂內容 Guid

如果尚未定義適當的命令內容 GUID，您可以在 VSPackage 中定義一個，然後視需要將它設為作用中或非作用中，以控制命令的可見度。 使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務執行下列動作：

- 註冊內容 Guid （藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 方法）。

- 取得內容 `GUID` 的狀態（藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法）。

- 開啟和關閉內容 `GUID`（藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 方法）。

    > [!CAUTION]
    > 請確定您的 VSPackage 不會影響任何現有內容 GUID 的狀態，因為其他 Vspackage 可能會相依于它們。

## <a name="example"></a>範例

下列 VSPackage 命令範例示範命令內容所管理之命令的動態可見度，而不會載入 VSPackage。

此命令會設定為在解決方案存在時啟用和顯示;也就是，只要下列其中一個命令內容 Guid 為作用中：

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

在此範例中，請注意每個命令旗標都是個別的[命令旗](../../extensibility/command-flag-element.md)標元素。

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

另請注意，每個 UI 內容都必須在個別的 `VisibilityItem` 元素中提供，如下所示。

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

## <a name="see-also"></a>請參閱

- [將命令新增至 [方案總管] 工具列](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)
- [以動態方式加入功能表項目](../../extensibility/dynamically-adding-menu-items.md)
