---
title: 新增工具列 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740226"
---
# <a name="add-a-toolbar"></a>新增工具列
本演練演示如何向可視化工作室 IDE 添加工具列。

 工具列是一個水準或垂直條帶,其中包含綁定到命令的按鈕。 根據其實現,IDE 中的工具列可以重新置放、停靠在主IDE視窗的任何一側,或使其位於其他視窗的前面。

 此外,用戶可以向工具列添加命令,或使用 **「自訂」** 對話方塊將其從工具列中刪除。 通常,VS 組包中的工具列是使用者可自定義的。 IDE 處理所有自定義,VS包回應命令。 VSPackage 不必知道命令的物理位置。

 關於選單的詳細資訊,請參閱[指令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-toolbar"></a>使用工具列建立延伸
 創建名為的`IDEToolbar`VSIX 專案。 添加名為**工具列測試命令 的**功能表命令項範本。 關於如何執行此操作的資訊,請參考[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

## <a name="create-a-toolbar-for-the-ide"></a>為 IDE 建立工具列

1. 在*工具列TestCommandPackage.vsct 中*,查找「符號」部分。 在名為 GuidToolbarTestCommandPackageCmdSet 的 GuidSymbol 元素中,添加工具列和工具列組的聲明,如下所示。

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. 在"命令"部分的頂部,創建功能表部分。 向"選單"部分添加"功能表"元素以定義工具列。

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

     工具列不能像子功能表一樣嵌套。 因此,您不必分配父組。 此外,您不必設置優先順序,因為用戶可以移動工具列。 通常,工具列的初始放置以程式設計方式定義,但使用者的後續更改將保持不變。

3. 在現有組項目之後的[「組](../extensibility/groups-element.md)」部分中,定義一個[組](../extensibility/group-element.md)元素以包含工具列的命令。

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. 使按鈕顯示在工具列上。 在「按鈕」部分中,將「按鈕」中的父塊替換為工具列。 產生的按鈕塊應如下所示:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     默認情況下,如果工具列沒有命令,則不會顯示。

5. 建置此專案並開始偵錯。 應出現實驗實例。

6. 右鍵按下「視覺工作室」功能表欄可獲取工具列清單。 選擇**測試工具列**。

7. 現在,您應該將工具列視為"在檔中尋找「圖示右側的圖示。 單擊該圖示時,應看到一個顯示**工具列TestCommandPackage的消息框。IDE 工具列內.工具列測試命令.Menuitem 回撥()**.

## <a name="see-also"></a>另請參閱
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
