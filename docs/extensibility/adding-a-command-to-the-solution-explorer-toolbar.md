---
title: 將命令加入至方案總管的工具列 |Microsoft Docs
description: 瞭解如何將執行命令的按鈕新增至 Visual Studio 中的方案總管工具列。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aa75bd1a229be147e3462845a61266a650e072e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900233"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>將命令新增至方案總管的工具列
本逐步解說將示範如何將按鈕新增至 **方案總管** 工具列。

 工具列或功能表上的任何命令都稱為 Visual Studio 中的按鈕。 按一下按鈕時，就會執行命令處理常式中的程式碼。 通常會將相關的命令群組在一起，以形成一個群組。 功能表或工具列可作為群組的容器。 優先權決定群組中個別命令出現在功能表或工具列上的順序。 您可以藉由控制控制項的可見度，防止按鈕顯示在工具列或功能表上。 .Vsct 檔案的區段中所列的命令 `<VisibilityConstraints>` 只會出現在相關聯的內容中。 可見度無法套用至群組。

 如需功能表、工具列命令和 *.vsct* 檔案的詳細資訊，請參閱 [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

> [!NOTE]
> 使用 XML 命令表格 (*. .vsct*) 檔案，而非命令表格設定 (*. .ctc*) 檔案，以定義功能表和命令在 vspackage 中出現的方式。 如需詳細資訊，請參閱 [Visual Studio 命令表格 (。.Vsct) ](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-menu-command"></a>使用功能表命令建立擴充功能
 建立名為的 VSIX 專案 `SolutionToolbar` 。 加入名為 **ToolbarButton** 的功能表命令專案範本。 如需有關如何進行此作業的詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>將按鈕新增至方案總管的工具列
 本逐步解說的這個部分會示範如何將按鈕加入至 **方案總管** 的工具列。 按一下按鈕時，就會執行回呼方法中的程式碼。

1. 在 *ToolbarButtonPackage. .vsct* 檔案中，移至  `<Symbols>` 一節。 `<GuidSymbol>`節點包含封裝範本所產生的功能表群組和命令。 將專案新增 `<IDSymbol>` 至此節點，以宣告將會保存您命令的群組。

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. 在 [ `<Groups>` 現有群組] 專案後面的區段中，定義您在上一個步驟中宣告的新群組。

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     將父 GUID： ID 組設定為， `guidSHLMainMenu` 並將 `IDM_VS_TOOL_PROJWIN` 這個群組放在 **方案總管** 的工具列上，設定高優先順序的值會將它放在其他命令群組之後。

3. 在 `<Buttons>` 區段中，變更所產生專案的父識別碼， `<Button>` 以反映您在上一個步驟中定義的群組。 修改過的 `<Button>` 元素看起來應該像這樣：

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. 建置此專案並開始偵錯。 實驗實例隨即出現。

     **方案總管** 的工具列應該會顯示現有按鈕右邊的 [新命令] 按鈕。 按鈕圖示是刪除線。

5. 按一下 [新增] 按鈕。

     應該會顯示一個對話方塊，其中包含在 **SolutionToolbar 中 ToolbarButtonPackage 的訊息。 ToolbarButton. MenuItemCallback ()** 。

## <a name="control-the-visibility-of-a-button"></a>控制按鈕的可見度
 本逐步解說的這個部分會示範如何控制工具列上按鈕的可見度。 藉由將內容設定為 SolutionToolbar. .vsct 檔案區段中的一或多個專案 `<VisibilityConstraints>` ，您就可以限制只有在專案或專案開啟時才會顯示按鈕。 

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>開啟一或多個專案時顯示按鈕

1. 在 `<Buttons>` *ToolbarButtonPackage* 的區段中，將兩個命令旗標新增至現有的 `<Button>` 元素，在 `<Strings>` 和 `<Icons>` 標記之間。

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    您 `DefaultInvisible` `DynamicVisibility` 必須設定和旗標，才能讓區段中的專案生效 `<VisibilityConstraints>` 。

2. 建立 `<VisibilityConstraints>` 具有兩個專案的區段 `<VisibilityItem>` 。 將新區段放在結束記號之後 `</Commands>` 。

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    每個可見度專案都代表一種條件，在這種情況下，會顯示指定的按鈕。 若要套用多個條件，您必須為相同的按鈕建立多個專案。

3. 建置此專案並開始偵錯。 實驗實例隨即出現。

    **方案總管** 的工具列未包含刪除線按鈕。

4. 開啟任何包含專案的方案。

    刪除線按鈕會出現在現有按鈕右邊的工具列上。

5. 按一下 [ **檔案** ] 功能表上的 [ **關閉方案**]。 按鈕會從工具列中消失。

   在載入 VSPackage 之前，會控制按鈕的可見度 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 載入 VSPackage 之後，按鈕的可見度是由 VSPackage 所控制。  如需詳細資訊，請參閱 [menucommand 對比與 OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)。

## <a name="see-also"></a>另請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)