---
title: 將功能表新增至 Visual Studio 的功能表列 |Microsoft Docs
description: 瞭解如何將功能表新增至 Visual Studio 整合式開發環境 (IDE) 的功能表列。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bd568e53c3a74819f642f0593524b314e065afb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951559"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>將功能表新增至 Visual Studio 的功能表列

本逐步解說將示範如何將功能表新增至 Visual Studio 整合式開發環境 (IDE) 的功能表列。 IDE 功能表列包含功能表 **類別，例如**[檔案]、[**編輯**]、[**視圖**]、[**視窗]****和 [** 說明]。

將新的功能表新增至 Visual Studio 的功能表列之前，請考慮是否要將命令放在現有的功能表中。 如需命令放置的詳細資訊，請參閱 [Visual Studio 的功能表和命令](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。

功能表是在專案的 *.vsct* 檔案中宣告的。 如需功能表和 *.vsct* 檔案的詳細資訊，請參閱 [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

完成此逐步解說之後，您就可以建立一個名為 [ **測試] 功能表** 的功能表，其中包含一個命令。

:::moniker range=">=vs-2019"
> [!NOTE]
> 從 Visual Studio 2019 開始，擴充功能所貢獻的最上層功能表會放置在 [ **延伸** 模組] 功能表下。
:::moniker-end

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>建立具有自訂命令專案範本的 VSIX 專案

1. 建立名為的 VSIX 專案 `TopLevelMenu` 。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。  如需詳細資訊，請參閱 [使用功能表命令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)模組。

::: moniker range="vs-2017"

2. 當專案開啟時，加入名為 **TestCommand** 的自訂命令專案範本。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >   **新專案**]。 在 [ **加入新專案** ] 對話方塊中，移至 **Visual c #/** 擴充性，然後選取 [ **自訂命令**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 *TestCommand.cs*。

::: moniker-end

::: moniker range=">=vs-2019"

2. 當專案開啟時，加入名為 **TestCommand** 的自訂命令專案範本。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >   **新專案**]。 在 [ **加入新專案** ] 對話方塊中，移至 [ **Visual c #/** 擴充性]，然後選取 [ **命令**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 *TestCommand.cs*。

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>在 IDE 功能表列上建立功能表

::: moniker range="vs-2017"

1. 在 **方案總管** 中，開啟 *TestCommandPackage .vsct*。

    在檔案結尾，有一個 `<Symbols>` 節點包含數個 `<GuidSymbol>` 節點。 在名為的節點中 `guidTestCommandPackageCmdSet` ，加入新的符號，如下所示：

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. `<Menus>`在節點中建立空白節點 `<Commands>` ，就在前面 `<Groups>` 。 在 `<Menus>` 節點中，新增 `<Menu>` 節點，如下所示：

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`功能表的和值會指定命令集 `id` ，以及命令集中的特定功能表。

    `guid`父位置的和值，在 `id` 包含 [工具] 和 [增益集] 功能表的 [Visual Studio] 功能表列的區段上。

    `<ButtonText>`元素會指定文字應出現在功能表項目中。

3. 在 `<Groups>` 區段中，尋找 `<Group>` 並變更元素， `<Parent>` 以指向我們剛剛新增的功能表：

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    這會讓群組成為新功能表的一部分。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 **方案總管** 中，開啟 *TopLevelMenuPackage .vsct*。

    在檔案結尾，有一個 `<Symbols>` 節點包含數個 `<GuidSymbol>` 節點。 在名為的節點中 `guidTopLevelMenuPackageCmdSet` ，加入新的符號，如下所示：

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. `<Menus>`在節點中建立空白節點 `<Commands>` ，就在前面 `<Groups>` 。 在 `<Menus>` 節點中，新增 `<Menu>` 節點，如下所示：

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`功能表的和值會指定命令集 `id` ，以及命令集中的特定功能表。

    `guid`父位置的和值，在 `id` 包含 [工具] 和 [增益集] 功能表的 [Visual Studio] 功能表列的區段上。

    `<ButtonText>`元素會指定文字應出現在功能表項目中。

3. 在 `<Groups>` 區段中，尋找 `<Group>` 並變更元素， `<Parent>` 以指向我們剛剛新增的功能表：

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    這會讓群組成為新功能表的一部分。

::: moniker-end

4. 在 `<Buttons>` 區段中，尋找 `<Button>` 節點。 然後，在 `<Strings>` 節點中，將 `<ButtonText>` 元素變更為 `Test Command` 。

    請注意， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 封裝範本所產生的 `Button` 元素會設定為的父元素 `MyMenuGroup` 。 因此，此命令會出現在功能表上。

## <a name="build-and-test-the-extension"></a>建立並測試擴充功能

1. 建置此專案並開始偵錯。 實驗實例的實例應該會出現。

::: moniker range="vs-2017"

2. 實驗實例中的功能表列應該包含 **測試功能表** 功能表。

::: moniker-end

::: moniker range=">=vs-2019"

2. 實驗實例中的 [ **延伸** 模組] 功能表應該包含 **測試功能表** 功能表。

::: moniker-end

3. 選取 [ **測試] 功能表** 功能表上的 [ **測試命令**]。

    應該會出現訊息方塊，並顯示「TestCommand 內部 TopLevelMenu. TestCommand. MenuItemCallback ( # A1」訊息。

## <a name="see-also"></a>另請參閱

- [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
