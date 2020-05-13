---
title: 向視覺工作室功能表欄添加功能表 |微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740305"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>向視覺工作室選單欄新增選單

本演練演示如何向 Visual Studio 整合式開發環境 (IDE) 的功能表列添加功能表。 IDE 選單列包含選單類別,如 **'檔案**'、"**編輯**"、"**查看**'、'**視窗**'**與'說明**"。

在將新功能表添加到 Visual Studio 選單欄之前,請考慮是否應將命令放置在現有功能表中。 有關命令放置的詳細資訊,請參閱[Visual Studio 的選單和指令](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。

選單在專案的 *.vsct*檔中聲明。 關於選單與 *.vsct*檔案的詳細資訊,請參閱[命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

通過完成本演練,您可以創建一個名為**TestMenu**的功能表,其中包含一個命令。

> [!NOTE]
> 在 VS 2019 中,由擴展提供的頂級功能表放在 **「擴展」** 選單下。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>建立具有自訂指令項目的 VSIX 專案

1. 創建名為的`TopLevelMenu`VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。  關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 打開專案時,添加名為**TestCommand**的自定義命令項範本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** >  **項**」。 在「**新增新項目」** 對話框中,轉到**可視化 C# / 擴充性**,然後選擇 **「自訂命令**」。 在視窗底部的**名稱「 欄**位中」,將指令檔名變更為*TestCommand.cs*。

## <a name="create-a-menu-on-the-ide-menu-bar"></a>在 IDE 選單列建立選單

::: moniker range="vs-2017"

1. 在**解決方案資源管理員中**,開啟*測試指令套件.vsct*。

    在檔末尾,有一個\<符號>節點,其中包含\<多個 GuidSymbol>节点。 在名為 guidTestCommandPackageCmdSet 的節點中,添加一個新符號,如下所示:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. 在\<\<"組>"\<之前 ,在命令>節點中創建空菜單>節點。 在\<"菜單>節點"中,\<添加 功能表>節點,如下所示:

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

    功能表`guid`的`id`和值指定命令集和命令集中的特定功能表。

    父`guid`功能`id`表的和值將功能表放置在包含「工具和外接程式」功能表的 Visual Studio 功能表列部分。

    `CommandName`字串的值指定文本應出現在菜單項中。

3. 在「\<群組>」部分\<中 ,查找組>\<並更改 父>元素以指向我們剛剛添加的菜單:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    這使得組成為新功能表的一部分。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在**解決方案資源管理員中**,開啟*頂級選單包.vsct*。

    在檔末尾,有一個\<符號>節點,其中包含\<多個 GuidSymbol>节点。 在名為 guidTopLevelMenuPackageCmdSet 的節點中,添加一個新符號,如下所示:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. 在\<\<"組>"\<之前 ,在命令>節點中創建空菜單>節點。 在\<"菜單>節點"中,\<添加 功能表>節點,如下所示:

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

    功能表`guid`的`id`和值指定命令集和命令集中的特定功能表。

    父`guid`功能`id`表的和值將功能表放置在包含「工具和外接程式」功能表的 Visual Studio 功能表列部分。

    `CommandName`字串的值指定文本應出現在菜單項中。

3. 在「\<群組>」部分\<中 ,查找組>\<並更改 父>元素以指向我們剛剛添加的菜單:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    這使得組成為新功能表的一部分。

::: moniker-end

4. 找出區段 `Buttons`。 請注意,[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]包範本已生成`Button`其 父`MyMenuGroup`設置為的元素。 因此,此命令將顯示在您的功能表上。

## <a name="build-and-test-the-extension"></a>組建及測試延伸

1. 建置此專案並開始偵錯。 應出現實驗實例的實例。

::: moniker range="vs-2017"

2. 實驗實體中的選單列應包含**TestMenu 選單**。

::: moniker-end

::: moniker range=">=vs-2019"

2. 實驗實體中的**延伸**選單應包含**TestMenu 選單**。

::: moniker-end

3. 在**測試功能表選**單上,按下 **「調用測試命令**」。

     應顯示一個消息框並顯示消息「頂級功能表中的測試命令包.TestCommand.MenuItem 回撥」」。

## <a name="see-also"></a>另請參閱

- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
