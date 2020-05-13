---
title: 使命令可用 |微軟文件
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
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707326"
---
# <a name="making-commands-available"></a>使命令可用

當將多個 VS 包添加到 Visual Studio 時,用戶介面 (UI) 可能會因命令而變得擁擠不堪。 您可以對包進行程式設計以幫助減少此問題,如下所示:

- 對包進行程式設計,使其僅在使用者需要時載入。

- 對包進行程式設計,以便僅當在整合式開發環境 (IDE) 的當前狀態上下文中可能需要命令時才顯示其命令。

## <a name="delayed-loading"></a>延遲載入

啟用延遲載入的典型方法是設計 VSPackage,以便其命令顯示在 UI 中,但在使用者按兩下其中一個命令之前不會載入套件本身。 為此,在 .vsct 檔案中,創建沒有命令標誌的命令。

下面的範例顯示了 .vsct 檔中功能表命令的定義。 這是選擇範本中的**功能表命令**選項時由可視化工作室包範本生成的命令。

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

在此示例中,如果父組`MyMenuGroup`('a) 是頂級功能表(如 **"工具"** 選單)的子級,則該命令將可見該功能表,但在使用者單擊該命令之前,不會載入執行該命令的包。 但是,通過程式設計命令來實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面,可以在首次展開包含該命令的菜單時啟用載入套件。

請注意,延遲載入還可以提高啟動性能。

## <a name="current-context-and-the-visibility-of-commands"></a>目前上下文與命令的可見度

您可以根據 VSPackage 資料的目前狀態或目前的相關的操作將 VSPackage 命令程式設計為可見或隱藏。 您可以使 VSPackage 能夠設定其命令的狀態,<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A><xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>通常使用介面中的方法的實現,但這需要載入 VSPackage 才能執行代碼。 相反,我們建議您使 IDE 能夠在不載入包的情況下管理命令的可見性。 為此,在 .vsct 檔中,將命令與一個或多個特殊 UI 上下文相關聯。 這些 UI 上下文由稱為*命令上下文 GUID*的 GUID 識別。

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]監視使用者操作(如載入專案或從編輯到生成)產生的更改。 當發生更改時,將自動修改 IDE 的外觀。 下表顯示了[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]監視的 IDE 更改的四個主要上下文。

| 內容類型 | 描述 |
|-------------------------| - |
| 活動項目類型 | 對於大多數項目類型,此值`GUID`與實現專案的 VSPackage 的 GUID 相同。 但是,[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案使用項目`GUID`類型 作為值。 |
| 作用視窗 | 通常,這是為金鑰綁定建立當前 UI 上下文的最後一個活動文件視窗。 但是,它也可以是一個工具視窗,具有類似於內部 Web 瀏覽器的密鑰綁定表。 對多選項卡文件視窗(如 HTML 編輯器),每個選項卡都具有不同的命令`GUID`上下文 。 |
| 活動語言服務 | 與目前顯示在文字編輯器中的文件關聯的語言服務。 |
| 活動工具視窗 | 打開且具有焦點的工具視窗。 |

第五個主要上下文區域是IDE的UI狀態。 UI 上下文由活動命令上下`GUID`文 標識,如下所示:

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

這些 GUID 標記為活動或非活動,具體取決於 IDE 的當前狀態。 多個 UI 上下文可以同時處於活動狀態。

### <a name="hide-and-display-commands-based-on-context"></a>以內容的文隱藏並顯示指令

您可以在 IDE 中顯示或隱藏包命令,而無需載入套件本身。 為此,`DefaultDisabled`請使用`DefaultInvisible``DynamicVisibility`、 和指令標誌,並將一個或多個[可見性專案](../../extensibility/visibilityitem-element.md)元素添加到[「可見性約束」](../../extensibility/visibilityconstraints-element.md)部分,從而定義套件的 .vsct 檔中的命令。 當指定的命令上下文`GUID`變為活動時,將顯示該命令而不載入包。

### <a name="custom-context-guids"></a>自訂內容介面

如果尚未定義適當的命令上下文 GUID,則可以在 VSPackage 中定義一個,然後根據需要將其程式設計為活動或非活動,以控制命令的可見性。 使用該服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>:

- 註冊上下文 GUID(通過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>用 方法)。

- 獲取上下文`GUID`的狀態(通過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>用 方法)。

- 打開和關閉上下文`GUID`(通過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>用 方法)。

    > [!CAUTION]
    > 請確保您的 VS 包不會影響任何現有上下文 GUID 的狀態,因為其他 VS 包可能依賴於它們。

## <a name="example"></a>範例

下面的 VSPackage 命令示例演示了由命令上下文管理而不載入 VSPackage 的命令的動態可見性。

命令設置為在存在解決方案時啟用和顯示;即,每當以下命令上下文之一處於活動狀態時:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

在此示例中,請注意每個命令標誌都是單獨的[命令標誌](../../extensibility/command-flag-element.md)元素。

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

另請注意,每個 UI 上下文都必須在`VisibilityItem`單獨的 元素中提供,如下所示。

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

- [新增解決方案資源管理員工具列新增命令](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [在 VSPackage 中路由傳送命令](../../extensibility/internals/command-routing-in-vspackages.md)
- [以動態方式加入功能表項目](../../extensibility/dynamically-adding-menu-items.md)
