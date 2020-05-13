---
title: 向解決方案資源管理員工具列加入指令 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740343"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>新增解決方案資源管理員工具列新增命令
本演練演示如何向**解決方案資源管理員**工具列添加按鈕。

 工具列或功能表上的任何命令都稱為 Visual Studio 中的按鈕。 按下該按鈕時,將執行命令處理程式中的代碼。 通常,相關命令被分組到一個組。 功能表或工具列充當組的容器。 優先順序確定組中單個命令在功能表或工具列上顯示的順序。 您可以通過控制按鈕的可見性來防止按鈕顯示在工具列或功能表上。 在 *.vsct*檔`<VisibilityConstraints>`部分中列出的命令僅在關聯的上下文中顯示。 可見性不能應用於組。

 關於選單、工具列指令與 *.vsct*檔案的詳細資訊,請參閱[命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

> [!NOTE]
> 使用 XML 命令表 *(.vsct*) 檔案而不是命令表配置 *(.ctc*) 檔案來定義選單和命令在 VS 套件中的顯示方式。 有關詳細資訊,請參閱[可視化工作室命令表 (。Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-menu-command"></a>使用選單指令建立延伸
 創建名為的`SolutionToolbar`VSIX 專案。 添加名為**工具列按鈕**的功能表命令項範本。 關於如何執行此操作的資訊,請參考[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>新增解決方案資源管理員工具列新增按鈕
 本演練的這一部分演示如何向**解決方案資源管理員**工具列添加按鈕。 按下該按鈕時,將運行回調方法中的代碼。

1. 在*工具列Button包.vsct*檔中,轉`<Symbols>`到該 部分。 該`<GuidSymbol>`節點包含包範本生成的功能表組和命令。 向此`<IDSymbol>`節點添加一個元素,以聲明將保存命令的組。

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. 在「`<Groups>`部份中,在現有組條目之後,定義您在上一步中聲明的新組。

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     將父 GUID:ID`guidSHLMainMenu`對`IDM_VS_TOOL_PROJWIN`設置為 並將此組放在**解決方案資源管理器**工具列上,並設置高優先順序值將其置於其他命令組之後。

3. 在本節`<Buttons>`中,更改生成`<Button>`的 條目的父 ID 以反映您在上一步中定義的組。 變更後`<Button>`的 元素應如下所示:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. 建置此專案並開始偵錯。 出現實驗實例。

     **解決方案資源管理員**工具列應在現有按鈕的右側顯示新的命令按鈕。 按鈕圖示是擊穿。

5. 按一下新按鈕。

     應顯示一個對話框,其中包含消息工具列**按鈕組(解決方案工具列.工具列.MenuItem 回調)。**

## <a name="control-the-visibility-of-a-button"></a>控制按鈕的可見度
 演練的這一部分演示如何控制工具列上按鈕的可見性。 通過在`<VisibilityConstraints>`*解決方案工具列.vsct*檔部分中設置上下文到一個或多個專案,可以將按鈕限制為僅在專案或項目打開時顯示。

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>開啟一個或多個項目時顯示按鈕

1. 在`<Buttons>`*工具列ButtonPackage.vsct*部分中,`<Button>``<Strings>`在`<Icons>`和標記之間向現有元素添加兩個命令標誌。

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    必須`DefaultInvisible`設置`DynamicVisibility`和標誌,以便節中的`<VisibilityConstraints>`條目可以生效。

2. 建立包含`<VisibilityConstraints>`兩`<VisibilityItem>`個條目的節。 將新部分放在結束`</Commands>`標記之後。

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

    每個可見性項表示顯示指定按鈕的條件。 要應用多個條件,必須為同一按鈕創建多個條目。

3. 建置此專案並開始偵錯。 出現實驗實例。

    **解決方案資源管理員**工具列不包含打擊按鈕。

4. 打開包含專案的任何解決方案。

    打擊按鈕將顯示在現有按鈕右側的工具列上。

5. 按一下 [ **檔案** ] 功能表上的 [ **關閉方案**]。 該按鈕從工具列中消失。

   按鈕的可見性由控制[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],直到載入 VSPackage。 載入 VSPackage 後,按鈕的可見性由 VSPackage 控制。  有關詳細資訊,請參閱[選單指令與 OleMenu 命令](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)。

## <a name="see-also"></a>另請參閱
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
