---
title: 加入工具視窗加入工具列 ( A)微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740240"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>加入工具視窗加入工具列
本演練演示如何向工具視窗添加工具列。

 工具列是一個水準或垂直條帶,其中包含綁定到命令的按鈕。 工具視窗中工具列的長度始終與工具視窗的寬度或高度相同,具體取決於工具列停靠的位置。

 與 IDE 中的工具列不同,工具視窗中的工具列必須停靠,並且不能移動或自定義。 如果 VSPackage 是用 u 託管代碼編寫的,工具列可以停靠在任何邊緣。

 有關如何加入工具列的詳細資訊,請參閱[新增工具列](../extensibility/adding-a-toolbar.md)。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-toolbar-for-a-tool-window"></a>為工具視窗建立工具列

1. 創建名為 VSIX`TWToolbar`專案的 VSIX 專案,該專案具有名為**TWTestCommand**的選單命令和名為**TestToolWindow**的工具視窗。 關於詳細資訊,請參閱[使用選單指令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md),以及[使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)。 在添加工具視窗範本之前,需要添加命令項範本。

2. 在*TWTestCommandPackage.vsct 中*,查找符號部分。 在名為 guidTWTestCommandPackageCmdSet 的 GuidSymbol 節點中,聲明工具列和工具列組,如下所示。

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. 在`Commands`節的頂部,創建一`Menus`個節。 添加元素`Menu`以定義工具列。

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     工具列不能像子功能表一樣嵌套。 因此,您不必分配父級。 此外,您不必設置優先順序,因為用戶可以移動工具列。 通常,工具列的初始放置以程式設計方式定義,但使用者的後續更改將保持不變。

4. 在「組」部分中,定義一個組以包含工具列的命令。

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. 在「按鈕」部分中,將現有 Button 元素的父元素更改為工具列組,以便顯示工具列。

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     默認情況下,如果工具列沒有命令,則不會顯示。

     由於新工具列不會自動添加到工具視窗,因此必須顯式添加工具列。 下一節將討論這個部分。

## <a name="add-the-toolbar-to-the-tool-window"></a>將工具列加入工具視窗

1. 在*TWTestCommandPackageGuids.cs*添加以下行。

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. 在*TestToolWindow.cs*添加以下 using 語句。

    ```csharp
    using System.ComponentModel.Design;
    ```

3. 在 TestToolWindow 構造函數中添加以下行。

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>在工具視窗中測試工具列

1. 建置此專案並開始偵錯。 應出現可視化工作室實驗實例。

2. 在 **「查看/其他視窗」** 選單上,按下 **「測試工具視窗**」以顯示工具視窗。

     您應該在工具視窗的左上角看到一個工具列(它看起來像預設圖示),就在標題的正下方。

3. 在工具列上,按一下該圖示以在**TWToolbar.TWTestCommand.Menu 專案回撥() 中顯示消息 TWTestCommandPackage。**

## <a name="see-also"></a>另請參閱
- [新增工具列](../extensibility/adding-a-toolbar.md)
