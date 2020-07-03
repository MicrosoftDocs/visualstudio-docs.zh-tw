---
title: 加入工具列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: beb97356daf3c932470bf2598e58e1f5b40ea233
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904073"
---
# <a name="add-a-toolbar"></a>新增工具列
本逐步解說示範如何將工具列新增至 Visual Studio IDE。

 工具列是水準或垂直的帶狀，其中包含系結至命令的按鈕。 根據其執行方式而定，IDE 中的工具列可以重新置放、停駐在主要 IDE 視窗的任一側，或留在其他視窗的前方。

 此外，使用者可以使用 [**自訂**] 對話方塊，將命令新增至工具列，或將其從其中移除。 一般而言，Vspackage 中的工具列可由使用者自訂。 IDE 會處理所有的自訂專案，而 VSPackage 會回應命令。 VSPackage 不需要知道命令實際上所在的位置。

 如需功能表的詳細資訊，請參閱[命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-toolbar"></a>使用工具列建立擴充功能
 建立名為的 VSIX 專案 `IDEToolbar` 。 新增名為**ToolbarTestCommand**的功能表命令專案範本。 如需如何執行此動作的詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

## <a name="create-a-toolbar-for-the-ide"></a>建立 IDE 的工具列

1. 在 [ *ToolbarTestCommandPackage .vsct*] 中，尋找 [符號] 區段。 在名為 guidToolbarTestCommandPackageCmdSet 的 GuidSymbol 元素中，新增工具列和工具列群組的宣告，如下所示。

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. 在 [命令] 區段的頂端，建立功能表區段。 將功能表項目新增至 [功能表] 區段，以定義您的工具列。

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     工具列不能像子功能表一樣嵌套。 因此，您不需要指派父群組。 此外，您不需要設定優先權，因為使用者可以移動工具列。 通常，會以程式設計方式定義工具列的初始位置，但會保存使用者的後續變更。

3. 在 [[群組](../extensibility/groups-element.md)] 區段中，于 [現有群組] 專案之後，定義 [[群組](../extensibility/group-element.md)] 元素以包含工具列的命令。

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. 讓按鈕顯示在工具列上。 在 [按鈕] 區段中，將按鈕中的父區塊取代為工具列。 產生的按鈕區塊看起來應該像這樣：

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     根據預設，如果工具列沒有任何命令，則不會出現。

5. 建置此專案並開始偵錯。 應該會出現實驗實例。

6. 以滑鼠右鍵按一下 [Visual Studio] 功能表列，以取得工具列清單。 選取 [**測試] 工具列**。

7. 您現在應該會看到工具列作為 [檔案中尋找] 圖示右邊的圖示。 當您按一下圖示時，您應該會看到一個訊息方塊，指出**ToolbarTestCommandPackage。在 IDEToolbar. ToolbarTestCommand. MenuItemCallback （）內**。

## <a name="see-also"></a>另請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
