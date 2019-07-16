---
title: 將功能表加入至功能表列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184932"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>將功能表新增至 Visual Studio 功能表列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何將 Visual Studio 整合式的開發環境 (IDE) 的功能表列中的功能表。 IDE 的功能表列包含功能表分類，例如**檔案**，**編輯**，**檢視**，**視窗**，以及**協助**.

 之前的 Visual Studio 功能表列中加入新的功能表，請考慮您的命令是否應該置於現有的功能表。 如需有關命令位置的詳細資訊，請參閱[功能表和命令適用於 Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。

 功能表是在.vsct 檔的專案中宣告。 如需功能表和.vsct 檔的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

 藉由完成這個逐步解說中，您可以建立名為功能表**TestMenu** ，其中包含一個命令。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>建立具有自訂命令項目範本的 VSIX 專案

1. 建立 VSIX 專案，名為`TopLevelMenu`。 您可以找到在 VSIX 專案範本**新的專案**下方的對話方塊**Visual C#**  / **擴充性**。  如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 當專案開啟時，新增名為的自訂命令項目範本**TestCommand**。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在 **加入新項目**對話方塊中，移至**Visual C# / 擴充性**，然後選取**自訂命令**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為**TestCommand.cs**。

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>在 IDE 的功能表列上建立功能表

#### <a name="to-create-a-menu"></a>建立功能表

1. 在 [**方案總管] 中**，開啟 TestCommandPackage.vsct。

     在檔案結尾，還有\<符號 > 節點，其中包含數個\<GuidSymbol > 節點。 在名為 guidTestCommandPackageCmdSet 節點，加入新的符號，如下所示：

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. 建立空\<功能表 > 中的節點\<命令 > 節點，之前\<群組 >。 在 \<功能表 > 節點，新增\<功能表 > 節點，如下所示：

    ```xml
    <Menus>
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
            <Parent guid="guidSHLMainMenu"
                    id="IDG_VS_MM_TOOLSADDINS" />
            <Strings>
              <ButtonText>TestMenu</ButtonText>
              <CommandName>TestMenu</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     `guid`和`id`功能表的值指定的命令集及特定的功能表中的命令集。

     `guid`和`id`父系值放置在 Visual Studio 功能表列，其中包含工具和增益集的功能表中的區段的功能表。

     值`CommandName`字串可讓您指定文字應該出現在功能表項目。

3. 在 \<群組 > 區段中，尋找\<群組 > 並變更\<父 > 指向我們剛才加入的功能表項目：

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     這可讓新的功能表中群組的一部分。

4. 尋找`Buttons`一節。 請注意，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]封裝範本所產生`Button`已設為其父代的項目`MyMenuGroup`。 如此一來，這個命令會出現在功能表上。

## <a name="building-and-testing-the-extension"></a>建置和測試擴充功能

1. 建置此專案並開始偵錯。 實驗執行個體的執行個體應該會出現。

2. 在實驗執行個體的功能表列應該包含**TestMenu**功能表。

3. 在  **TestMenu**功能表上，按一下**叫用測試命令**。

     訊息方塊應該會出現，並顯示訊息 「 第封裝頁，在 TopLevelMenu.TestCommand.MenuItemCallback() TestCommand"。 這表示，適用於新的命令。

## <a name="see-also"></a>另請參閱
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)
