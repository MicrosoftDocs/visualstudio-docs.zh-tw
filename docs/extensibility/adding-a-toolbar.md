---
title: 新增工具列 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0485b6649396239d2b6501c65e801a03767d5df1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891874"
---
# <a name="add-a-toolbar"></a>新增工具列
本逐步解說示範如何將工具列新增至 Visual Studio IDE。

 工具列是水平或垂直的區域，其中包含繫結至命令的按鈕。 根據它的實作，IDE 中的工具列可以重新定位、 停駐的主要 IDE 視窗中，任何一側或待前其他視窗。

 此外，使用者可以將命令加入至工具列，或移除它們，方法是使用**自訂** 對話方塊。 一般而言，在 Vspackage 中的工具列是使用者可自訂的。 IDE 會處理所有自訂項目，並回應命令的 VSPackage。 VSPackage 不必知道命令的實體所在的位置。

 如需功能表的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-toolbar"></a>建立具有工具列的延伸模組
 建立 VSIX 專案，名為`IDEToolbar`。 加入名為功能表命令項目範本**ToolbarTestCommand**。 如需如何執行這項操作的資訊，請參閱[建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="create-a-toolbar-for-the-ide"></a>Ide 中建立工具列

1. 在  *ToolbarTestCommandPackage.vsct*，尋求的 Symbols 區段。 在名為 guidToolbarTestCommandPackageCmdSet GuidSymbol 元素中，加入宣告一個工具列和工具列群組，如下所示。

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. 在 [命令] 區段頂端，建立功能表一節。 定義您的工具列的 [功能表] 區段中加入功能表項目。

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

     工具列不能巢狀，像是子功能表。 因此，您不必將父群組指派。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 一般而言，以程式設計的方式，定義工具列的初始位置，但使用者的後續變更會保存。

3. 在 [群組](../extensibility/groups-element.md)區段中，現有的群組項目之後, 定義[群組](../extensibility/group-element.md)来包含工具列命令項目。

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. 請在工具列上顯示的按鈕。 在 [按鈕] 區段中，將父系區塊，在工具列按鈕中。 產生按鈕區塊看起來應該像這樣：

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     根據預設，如果工具列上不有任何命令，它不會出現。

5. 建置此專案並開始偵錯。 實驗執行個體應該會出現。

6. 以滑鼠右鍵按一下 Visual Studio 功能表列，以取得工具列的清單。 選取 **測試工具列**。

7. 您現在應該看到圖示右邊的 [檔案] 圖示中尋找您的工具列。 當您按一下圖示時，您應該會看到出現訊息方塊，指出**ToolbarTestCommandPackage。Inside IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>另請參閱
- [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)