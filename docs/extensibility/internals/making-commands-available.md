---
title: 提供命令使用 |Microsoft 文件
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e20fd9b1b13dfc8159181ee2cb8f5d8966f6faf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="making-commands-available"></a>提供命令使用
當多個 Vspackage 加入至 Visual Studio 時，使用者介面 (UI) 可能會變得過擁擠命令。 您可以設計您的封裝，以協助降低這個問題，如下：

-   程式封裝，讓它在使用者時才會載入需要它。

-   程式封裝，使其命令才會顯示目前狀態的整合式的開發環境 (IDE) 的內容中可能會需要它們。

## <a name="delayed-loading"></a>延遲載入
 若要啟用的一般方法延遲載入為設計 VSPackage，使其命令會顯示在 UI 中，但封裝本身不會載入直到使用者按一下其中一個命令。 若要達成此目的，.vsct 檔中，建立不具有任何命令旗標的命令。

 下列範例顯示功能表命令.vsct 檔案中的定義。 這是 Visual Studio 封裝範本所產生的命令時**功能表命令**選取範本中的選項。

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

 在範例中，如果父群組， `MyMenuGroup`，是最上層功能表的子系，例如**工具**功能表上，此命令將會顯示在該功能表上，但將不會載入之封裝的執行命令，直到按下命令由使用者。 不過，以程式設計方式編寫來實作命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，您可以啟用要先展開包含命令的功能表時載入的封裝。

 請注意延遲的載入，也可以改善啟動效能。

## <a name="current-context-and-the-visibility-of-commands"></a>目前的內容和命令的可見性
 您可以程式設計 VSPackage 的命令是可見或隱藏，根據 VSPackage 資料或目前相關的動作的目前狀態。 您可以啟用 VSPackage 也可以設定它的命令的狀態通常使用的實作<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>方法從<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，但這需要才能執行程式碼要載入 VSPackage。 相反地，我們建議您啟用 IDE，才能管理命令的可見性，而不載入封裝。 若要這樣做，在.vsct 檔案中，請將命令與一或多個特殊的 UI 內容產生關聯。 這些 UI 內容由稱為 GUID 所識別*命令內容 GUID*。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 監視所產生的使用者動作，例如載入專案，或編輯要建置變更。 發生變更時，會自動修改 IDE 的外觀。 下表顯示四個主要的內容，IDE 的變更，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]監視器。

|內容的型別|描述|
|---------------------|-----------------|
|使用中的專案類型|對於大部分的專案類型，這`GUID`值時的 VSPackage 實作專案 GUID 相同。 不過，[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案使用 專案類型`GUID`做為值。|
|使用中視窗|一般而言，這是最後一個使用中的文件視窗所建立的索引鍵繫結的目前 UI 內容。 不過，它也可能是有一個索引鍵繫結資料表，類似於內部的 Web 瀏覽器工具視窗。 多個索引標籤的文件視窗 （例如 HTML 編輯器） 如每個索引標籤上會有不同的命令內容`GUID`。|
|作用中的語言服務|與目前顯示在文字編輯器中的檔案相關聯的語言服務。|
|使用中工具視窗|工具視窗已開啟且具有焦點。|

 第五個主要內容區域是 IDE 的 UI 狀態。 UI 內容所識別的作用中的命令內容`GUID`s，如下所示：

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

 這些 Guid 會標示為作用中或非使用中，根據在 IDE 的目前狀態。 多個 UI 內容可以在相同的時間。

### <a name="hiding-and-displaying-commands-based-on-context"></a>隱藏和顯示內容為基礎的命令
 您可以顯示或隱藏在 IDE 中的 [套件] 命令，而不載入封裝本身。 若要這樣做，請定義命令.vsct 檔的封裝中使用`DefaultDisabled`， `DefaultInvisible`，和`DynamicVisibility`命令旗標並新增一或多個[VisibilityItem](../../extensibility/visibilityitem-element.md)項目[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) > 一節。 當指定的命令內容`GUID`會變成作用中，此命令會顯示不含載入封裝。

### <a name="custom-context-guids"></a>自訂內容的 Guid
 如果未定義的 GUID 不適當的命令內容中，您可以定義一個 VSPackage 中，然後再將它設為作用中或非使用中，視需要控制命令的可見性程式。 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>服務：

-   註冊內容 Guid (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>方法)。

-   取得內容的狀態`GUID`(藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>方法)。

-   開啟內容`GUID`s 開啟和關閉 (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>方法)。

    > [!CAUTION]
    > 請確定，VSPackage 不會影響任何現有內容 GUID 的狀態因為其他 Vspackage 可能會取決於它們。

## <a name="example"></a>範例
 VSPackage 命令的下列範例會示範動態的可見性，而不必載入 VSPackage 的命令內容管理的命令。

 命令是設定為啟用，而且每當方案存在，顯示亦即，每當下列的命令內容 Guid 的其中一個是作用中：

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>

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

- [MenuCommand 對比OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)
- [以動態方式加入功能表項目](../../extensibility/dynamically-adding-menu-items.md)