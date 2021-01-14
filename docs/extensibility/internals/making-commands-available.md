---
title: 讓命令可供使用 |Microsoft Docs
description: 瞭解如何使用延遲的載入、內容和可見度，來控制在 Vspackage 中新增至 Visual Studio IDE 之命令的可用性。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d17fd0b63438183b10b1ecb0e5eb6abb9f5d7f46
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204531"
---
# <a name="making-commands-available"></a>讓命令可供使用

將多個 Vspackage 新增至 Visual Studio 時，使用者介面 (UI) 可能會變成使用命令 overcrowded。 您可以針對套件進行程式設計，以協助減少此問題，如下所示：

- 將封裝程式設計成隻在使用者需要時才載入。

- 編寫套件的程式，只在整合式開發環境 (IDE) 的目前狀態內容需要時，才會顯示其命令。

## <a name="delayed-loading"></a>延遲載入

啟用延遲載入的一般方式是設計 VSPackage，讓其命令顯示在 UI 中，但在使用者按一下其中一個命令之前，不會載入封裝本身。 若要完成此動作，請在 .vsct 檔案中建立沒有命令旗標的命令。

下列範例會顯示 .vsct 檔案中功能表命令的定義。 這是在選取範本中的 **功能表命令** 選項時，由 Visual Studio 套件範本產生的命令。

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

在此範例中，如果父群組 `MyMenuGroup` 是最上層功能表（例如 [ **工具** ] 功能表）的子系，則該命令會顯示在該功能表中，但在使用者按下命令之前，將不會載入執行命令的封裝。 不過，藉由程式設計命令來執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，您可以在第一次展開包含命令的功能表時，讓封裝載入。

請注意，延遲的載入也可以改善啟動效能。

## <a name="current-context-and-the-visibility-of-commands"></a>目前的內容和命令的可見度

您可以根據目前的 VSPackage 資料狀態或目前相關的動作，將 VSPackage 命令程式設計為可見或隱藏。 您可以啟用 VSPackage 來設定其命令的狀態（通常是藉由使用介面的方法實作為 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ），但這需要先載入 VSPackage，才能執行程式碼。 相反地，我們建議您啟用 IDE 來管理命令的可見度，而不需要載入封裝。 若要這樣做，請在 .vsct 檔案中，將命令與一或多個特殊的 UI 內容產生關聯。 這些 UI 內容是由稱為 *命令內容 guid* 的 guid 所識別。

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 監視使用者動作所產生的變更，例如載入專案或從編輯到建立。 發生變更時，會自動修改 IDE 的外觀。 下表顯示監視之 IDE 變更的四個主要內容 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

| 內容類型 | 描述 |
|-------------------------| - |
| 作用中的專案類型 | 針對大部分的專案類型，這個值與執行 `GUID` 專案之 VSPackage 的 GUID 相同。 不過， [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案會使用專案類型 `GUID` 作為值。 |
| 使用中視窗 | 通常，這是最後一個使用中的文件視窗，可建立目前的 UI 內容以進行索引鍵系結。 不過，它也可能是具有類似于內部網頁瀏覽器之按鍵系結表的工具視窗。 針對多索引標籤式文件視窗（例如 HTML 編輯器），每個索引標籤都有不同的命令內容 `GUID` 。 |
| 主動式語言服務 | 與目前在文字編輯器中顯示的檔案相關聯的語言服務。 |
| 作用中的工具視窗 | 開啟並具有焦點的工具視窗。 |

第五個主要內容區域是 IDE 的 UI 狀態。 UI 內容是由 active 命令內容所識別，如下所示 `GUID` ：

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

這些 Guid 會標示為作用中或非作用中，視 IDE 目前的狀態而定。 多個 UI 內容可以同時處於作用中狀態。

### <a name="hide-and-display-commands-based-on-context"></a>根據內容隱藏和顯示命令

您可以在 IDE 中顯示或隱藏封裝命令，而不需要載入封裝本身。 若要這樣做，請使用、和命令旗標，在封裝的 .vsct 檔案中定義命令， `DefaultDisabled` `DefaultInvisible` `DynamicVisibility` 然後將一或多個 [VisibilityItem](../../extensibility/visibilityitem-element.md) 專案加入至 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 區段。 當指定的命令內容 `GUID` 變成作用中時，就會顯示命令，而不會載入封裝。

### <a name="custom-context-guids"></a>自訂內容 Guid

如果未定義適當的命令內容 GUID，您可以在 VSPackage 中定義一個，然後視需要將其設計為作用中或非作用中，以控制命令的可見度。 使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 服務：

- 藉由呼叫方法) 來註冊內容 Guid (<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 。

- 藉 `GUID` 由呼叫) 方法，取得內容 (的狀態 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 。

- 藉 `GUID` 由呼叫方法) ，開啟和關閉 (的內容 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 。

    > [!CAUTION]
    > 請確定您的 VSPackage 不會影響任何現有內容 GUID 的狀態，因為其他 Vspackage 可能相依于這些 GUID。

## <a name="example"></a>範例

下列 VSPackage 命令範例會示範命令內容所管理的命令動態可見度，而不需要載入 VSPackage。

此命令會設定為在解決方案存在時啟用和顯示;也就是說，每當下列其中一個命令內容 Guid 為作用中時：

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

在此範例中，請注意，每個命令旗標都是個別的 [命令旗](../../extensibility/command-flag-element.md) 標元素。

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

另請注意，每個 UI 內容都必須在個別的元素中指定，如下所示 `VisibilityItem` 。

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

- [將命令新增至方案總管的工具列](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)
- [以動態方式加入功能表項目](../../extensibility/dynamically-adding-menu-items.md)
