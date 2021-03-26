---
title: 將工具列新增至工具視窗 |Microsoft Docs
description: 瞭解如何在 (IDE) 的 Visual Studio 整合式開發環境中，將包含系結至命令之按鈕的工具列加入至工具視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1847801ed9dcbb1b7c7145c86b1998b54e2bb5d9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055787"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>將工具列新增至工具視窗
本逐步解說將說明如何將工具列加入至工具視窗。

 工具列是包含與命令系結之按鈕的水準或垂直帶狀。 工具視窗中的工具列長度一律與工具視窗的寬度或高度相同，視工具列的停駐位置而定。

 不同于 IDE 中的工具列，工具視窗中的工具列必須固定，而且無法移動或自訂。 如果 VSPackage 是以 umanaged 程式碼撰寫，工具列可停駐在任何邊緣。

 如需如何加入工具列的詳細資訊，請參閱 [加入工具列](../extensibility/adding-a-toolbar.md)。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-toolbar-for-a-tool-window"></a>建立工具視窗的工具列

1. 建立名為的 VSIX 專案 `TWToolbar` ，這個專案具有名為 **TWTestCommand** 的功能表命令和名為 **TestToolWindow** 的工具視窗。 如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md) 模組和 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。 您必須先加入命令專案範本，才能加入工具視窗範本。

2. 在 *TWTestCommandPackage. .vsct* 中，尋找 [符號] 區段。 在名為 guidTWTestCommandPackageCmdSet 的 GuidSymbol 節點中，宣告工具列和工具列群組，如下所示。

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. 在區段的頂端 `Commands` ，建立一個 `Menus` 區段。 加入 `Menu` 元素來定義工具列。

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

     工具列不能像子功能表一樣地嵌套。 因此，您不需要指派父系。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 通常，會以程式設計的方式定義工具列的初始位置，但是會保存使用者的後續變更。

4. 在 [群組] 區段中，定義包含工具列命令的群組。

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. 在 [按鈕] 區段中，將現有按鈕元素的父系變更為工具列群組，以便顯示工具列。

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     依預設，如果工具列沒有任何命令，則不會出現。

     因為新的工具列不會自動加入至工具視窗，所以必須明確加入工具列。 下一節將討論這個部分。

## <a name="add-the-toolbar-to-the-tool-window"></a>將工具列新增至工具視窗

1. 在 *TWTestCommandPackageGuids* 中，新增下列幾行。

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. 在 *TestToolWindow* 中，新增下列 using 語句。

    ```csharp
    using System.ComponentModel.Design;
    ```

3. 在 TestToolWindow 的函式中，加入下列程式程式碼。

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>在工具視窗中測試控管欄

1. 建置此專案並開始偵錯。 應該會出現 Visual Studio 實驗實例。

2. 在 [ **視圖]/[其他視窗** ] 功能表上，按一下 [ **測試控管視窗** ] 以顯示工具視窗。

     您應該會看到工具列 (看起來像是工具視窗左上角的預設圖示) ，緊接在標題正下方。

3. 在工具列上，按一下圖示以顯示 [TWToolbar] **() 內的訊息 TWTestCommandPackage。 TWTestCommand. MenuItemCallback**。

## <a name="see-also"></a>另請參閱
- [新增工具列](../extensibility/adding-a-toolbar.md)
