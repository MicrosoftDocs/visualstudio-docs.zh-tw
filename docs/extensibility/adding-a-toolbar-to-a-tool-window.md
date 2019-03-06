---
title: 新增工具列加入工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b2cfcc4662bff6b404e331a4329edaefd245df0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695618"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>將工具列加入工具視窗
本逐步解說示範如何將工具列加入工具視窗。

 工具列是水平或垂直的區域，其中包含繫結至命令的按鈕。 中的工具視窗的工具列長度一律為相同的寬度或高度的 [工具] 視窗中，根據工具列停駐的位置。

 不同於在 IDE 中的 [工具列]，工具視窗中的工具列必須停駐和無法移動或自訂。 如果 VSPackage 以 umanaged 程式碼撰寫，則可以停駐工具列任何一邊上。

 如需如何加入工具列的詳細資訊，請參閱[新增工具列](../extensibility/adding-a-toolbar.md)。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-toolbar-for-a-tool-window"></a>建立工具視窗工具列

1.  建立 VSIX 專案，名為`TWToolbar`具有名為這兩個功能表命令**TWTestCommand**一個名為的工具視窗**TestToolWindow**。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)並[建立工具視窗的延伸模組](../extensibility/creating-an-extension-with-a-tool-window.md)。 您需要加入命令項目範本加入工具視窗範本之前。

2.  在  *TWTestCommandPackage.vsct*，尋求的 Symbols 區段。 在名為 guidTWTestCommandPackageCmdSet GuidSymbol 節點應宣告一個工具列和工具列群組，如下所示。

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3.  在頂端`Commands`區段中，建立`Menus`一節。 新增`Menu`項目來定義工具列。

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

     工具列不能巢狀，像是子功能表。 因此，您不需要將父代。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 一般而言，以程式設計的方式，定義工具列的初始位置，但使用者的後續變更會保存。

4.  在 [群組] 區段中，定義要包含工具列命令的群組。

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5.  在 [按鈕] 區段中，變更現有的按鈕項目的父工具列群組，使工具列會顯示。

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     根據預設，如果工具列上不有任何命令，它不會出現。

     因為新的工具列不會自動加入至 [工具] 視窗，就必須明確地加入工具列。 下一節將討論這個部分。

## <a name="add-the-toolbar-to-the-tool-window"></a>將工具列新增至 [工具] 視窗

1.  在  *TWTestCommandPackageGuids.cs*新增下列幾行。

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2.  在  *TestToolWindow.cs*新增下列 using 陳述式。

    ```csharp
    using System.ComponentModel.Design;
    ```

3.  TestToolWindow 建構函式中加入下面這一行。

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>工具視窗中的測試 工具列

1.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。

2.  上**檢視 / 其他 Windows**功能表上，按一下**測試 ToolWindow**顯示工具視窗。

     您應該會看到 （看起來像的預設圖示） 在頂端工具列方的 [工具] 視窗標題的正下方。

3.  在工具列上，按一下 顯示訊息圖示**TWTestCommandPackage 內 TWToolbar.TWTestCommand.MenuItemCallback()**。

## <a name="see-also"></a>另請參閱
- [新增工具列](../extensibility/adding-a-toolbar.md)