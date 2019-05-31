---
title: 將功能表加入至 Visual Studio 功能表列 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a28e7f69ed8e9a76e11d8892ee677435f75c99b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349785"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>將功能表加入 Visual Studio 功能表列

本逐步解說示範如何將 Visual Studio 整合式的開發環境 (IDE) 的功能表列中的功能表。 IDE 的功能表列包含功能表分類，例如**檔案**，**編輯**，**檢視**，**視窗**，以及**協助**.

之前的 Visual Studio 功能表列中加入新的功能表，請考慮您的命令是否應該置於現有的功能表。 如需有關命令位置的詳細資訊，請參閱[功能表和命令適用於 Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。

功能表中宣告 *.vsct*專案檔案。 如需功能表和 *.vsct*檔，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

藉由完成這個逐步解說中，您可以建立名為功能表**TestMenu** ，其中包含一個命令。

> [!NOTE]
> 在 VS 2019，由延伸模組所提供最上層功能表會放在**延伸模組**功能表。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>建立具有自訂命令項目範本的 VSIX 專案

1. 建立 VSIX 專案，名為`TopLevelMenu`。 您可以找到在 VSIX 專案範本**新的專案**藉由搜尋 「 vsix 」 的對話方塊。  如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的延伸模組](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 當專案開啟時，新增名為的自訂命令項目範本**TestCommand**。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** >  **新項目**。 在 **加入新項目**對話方塊中，移至**Visual C# / 擴充性**，然後選取**自訂命令**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為*TestCommand.cs*。

## <a name="create-a-menu-on-the-ide-menu-bar"></a>建立 IDE 的功能表列上的功能表

::: moniker range="vs-2017"

1. 在 **方案總管**，開啟*TestCommandPackage.vsct*。

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

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 **方案總管**，開啟*TopLevelMenuPackage.vsct*。

    在檔案結尾，還有\<符號 > 節點，其中包含數個\<GuidSymbol > 節點。 在名為 guidTopLevelMenuPackageCmdSet 節點，加入新的符號，如下所示：

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. 建立空\<功能表 > 中的節點\<命令 > 節點，之前\<群組 >。 在 \<功能表 > 節點，新增\<功能表 > 節點，如下所示：

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
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
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    這可讓新的功能表中群組的一部分。

::: moniker-end

4. 尋找`Buttons`一節。 請注意，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]封裝範本所產生`Button`已設為其父代的項目`MyMenuGroup`。 如此一來，此命令會出現在功能表上。

## <a name="build-and-test-the-extension"></a>建置並測試此擴充功能

1. 建置此專案並開始偵錯。 實驗執行個體的執行個體應該會出現。

::: moniker range="vs-2017"

2. 在實驗執行個體的功能表列應該包含**TestMenu**功能表。

::: moniker-end

::: moniker range=">=vs-2019"

2. **延伸模組**功能表中的實驗執行個體應該包含**TestMenu**功能表。

::: moniker-end

3. 在  **TestMenu**功能表上，按一下**叫用測試命令**。

     訊息方塊應該會出現，並顯示訊息 「 第封裝頁，在 TopLevelMenu.TestCommand.MenuItemCallback() TestCommand"。

## <a name="see-also"></a>另請參閱

- [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)