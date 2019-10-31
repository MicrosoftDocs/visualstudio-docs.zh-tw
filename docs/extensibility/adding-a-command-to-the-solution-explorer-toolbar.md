---
title: 將命令新增至 [方案總管] 工具列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99a21a4dd4c39a4cefdf6be30171c503fc2ce005
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187104"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>將命令新增至 [方案總管] 工具列
本逐步解說示範如何將按鈕新增至 [**方案總管**] 工具列。

 工具列或功能表上的任何命令都稱為 Visual Studio 中的按鈕。 按一下按鈕時，就會執行命令處理常式中的程式碼。 一般而言，相關的命令會群組在一起，以形成一個群組。 功能表或工具列扮演群組的容器。 [優先順序] 決定群組中個別命令出現在功能表或工具列上的順序。 您可以藉由控制按鈕的可見度，避免在工具列或功能表上顯示按鈕。 在 *.vsct*檔案的 `<VisibilityConstraints>` 區段中所列的命令，只會出現在相關聯的內容中。 可見度無法套用至群組。

 如需功能表、工具列命令及 *.vsct*檔的詳細資訊，請參閱[命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

> [!NOTE]
> 使用 XML 命令資料表（ *. .vsct*）檔案，而不是命令資料表設定（ *. .ctc*）檔案，以定義功能表和命令在 vspackage 中的顯示方式。 如需詳細資訊，請參閱[Visual Studio 命令資料表（）.Vsct）](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔案。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-menu-command"></a>使用功能表命令建立擴充功能
 建立名為 `SolutionToolbar`的 VSIX 專案。 新增名為**ToolbarButton**的功能表命令專案範本。 如需如何執行此動作的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>將按鈕新增至 [方案總管] 工具列
 本逐步解說的這一節將示範如何將按鈕新增至 [**方案總管**] 工具列。 按一下按鈕時，就會執行回呼方法中的程式碼。

1. 在*ToolbarButtonPackage. .vsct*檔案中，移至 [`<Symbols>`] 區段。 [`<GuidSymbol>`] 節點包含封裝範本所產生的功能表群組和命令。 將 `<IDSymbol>` 專案新增至此節點，以宣告會保存命令的群組。

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. 在 [`<Groups>`] 區段中，于 [現有群組] 專案之後，定義您在上一個步驟中宣告的新群組。

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     將父 GUID： ID 組設定為 `guidSHLMainMenu` 並 `IDM_VS_TOOL_PROJWIN` 將此群組放在 [**方案總管**] 工具列上，並設定高優先順序的值，將它放在其他命令群組之後。

3. 在 [`<Buttons>`] 區段中，變更所產生 `<Button>` 專案的父識別碼，以反映您在上一個步驟中定義的群組。 修改過的 `<Button>` 元素看起來應該像這樣：

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

     [**方案總管**] 工具列應該會顯示現有按鈕右邊的 [新增命令] 按鈕。 按鈕圖示是刪除線。

5. 按一下 [新增] 按鈕。

     應該會顯示在 [SolutionToolbar] **ToolbarButton MenuItemCallback （）內已 ToolbarButtonPackage**訊息的對話方塊。

## <a name="control-the-visibility-of-a-button"></a>控制按鈕的可見度
 本逐步解說的這一節將示範如何控制工具列上按鈕的可見度。 藉由在*SolutionToolbar*檔案的 [`<VisibilityConstraints>`] 區段中，將內容設定為一個或多個專案，您可以限制只有在開啟專案或專案時才會顯示按鈕。

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>若要在一或多個專案開啟時顯示按鈕

1. 在*ToolbarButtonPackage*的 [`<Buttons>`] 區段中，將兩個命令旗標加入至現有的 `<Button>` 元素，`<Strings>` 和 `<Icons>` 標記之間。

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    必須設定 `DefaultInvisible` 和 `DynamicVisibility` 旗標，`<VisibilityConstraints>` 區段中的專案才會生效。

2. 建立具有兩個 `<VisibilityItem>` 專案的 `<VisibilityConstraints>` 區段。 將新的區段放在結尾 `</Commands>` 標記的正後方。

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

    每個可見度專案都代表顯示指定按鈕所依據的條件。 若要套用多個條件，您必須為相同的按鈕建立多個專案。

3. 建置此專案並開始偵錯。 實驗實例隨即出現。

    [**方案總管**] 工具列不包含 [刪除線] 按鈕。

4. 開啟任何包含專案的方案。

    [刪除線] 按鈕會出現在現有按鈕右邊的工具列上。

5. **在 [檔案**] 功能表上，按一下 [**關閉方案**]。 按鈕會從工具列中消失。

   在載入 VSPackage 之前，會 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 控制按鈕的可見度。 載入 VSPackage 之後，按鈕的可見度是由 VSPackage 所控制。  如需詳細資訊，請參閱[menucommand 對比與 OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)。

## <a name="see-also"></a>請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)