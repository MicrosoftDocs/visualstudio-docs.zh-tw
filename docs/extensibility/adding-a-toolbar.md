---
title: 加入工具列 |Microsoft Docs
description: 瞭解如何將包含按鈕的工具列，加入至 Visual Studio 整合式開發環境 (IDE) 的命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62d32a07ec046bc42d69818346450e5a94a668ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951325"
---
# <a name="add-a-toolbar"></a>新增工具列
本逐步解說將示範如何將工具列加入 Visual Studio IDE。

 工具列是包含系結至命令之按鈕的水準或分隔號紋。 根據其執行方式，IDE 中的工具列可以重新置放、停駐于主要 IDE 視窗的任何一端，或保持在其他視窗前方。

 此外，使用者可以使用 [ **自訂** ] 對話方塊，將命令加入至工具列或從中移除。 一般而言，Vspackage 中的工具列可供使用者自訂。 IDE 會處理所有自訂，而 VSPackage 會回應命令。 VSPackage 不需要知道命令實際所在的位置。

 如需功能表的詳細資訊，請參閱 [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-toolbar"></a>使用工具列建立延伸模組
 建立名為的 VSIX 專案 `IDEToolbar` 。 加入名為 **ToolbarTestCommand** 的功能表命令專案範本。 如需有關如何進行此作業的詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

## <a name="create-a-toolbar-for-the-ide"></a>建立 IDE 的工具列

1. 在 *ToolbarTestCommandPackage. .vsct* 中，尋找 [符號] 區段。 在名為 guidToolbarTestCommandPackageCmdSet 的 GuidSymbol 元素中，加入工具列和工具列群組的宣告，如下所示。

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

     工具列不能像子功能表一樣地嵌套。 因此，您不需要指派父群組。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 通常，會以程式設計的方式定義工具列的初始位置，但是會保存使用者的後續變更。

3. 在 [ [群組](../extensibility/groups-element.md) ] 區段的 [現有群組] 專案之後，定義一個 [群組](../extensibility/group-element.md) 專案以包含工具列的命令。

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. 讓按鈕出現在工具列上。 在 [按鈕] 區段中，將按鈕中的父區塊取代為工具列。 產生的按鈕區塊看起來應該像這樣：

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     依預設，如果工具列沒有任何命令，則不會出現。

5. 建置此專案並開始偵錯。 實驗實例應會出現。

6. 以滑鼠右鍵按一下 Visual Studio 的功能表列，以取得工具列清單。 選取 [ **測試] 工具列**。

7. 您現在應該會看到工具列顯示為 [檔案中尋找] 圖示右邊的圖示。 當您按一下圖示時，應該會看到一個訊息方塊，指出 **ToolbarTestCommandPackage。在 IDEToolbar 中，ToolbarTestCommand. MenuItemCallback ( # B1**。

## <a name="see-also"></a>另請參閱
- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
