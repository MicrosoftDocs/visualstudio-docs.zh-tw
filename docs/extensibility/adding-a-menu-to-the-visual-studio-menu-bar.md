---
title: "將功能表加入至 Visual Studio 功能表列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建立最上層的功能表"
  - "最上層功能表"
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 51
---
# 將功能表加入至 Visual Studio 功能表列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說示範如何將功能表加入 Visual Studio 整合式的開發環境 \(IDE\) 的功能表列。 IDE 的功能表列包含功能表類別，例如 **檔案**, ，**編輯**, ，**檢視**, ，**視窗**, ，和 **協助**。  
  
 之前將新的功能表加入至 Visual Studio 功能表列，請考慮是否要將命令放在現有的功能表內。 如需命令位置的詳細資訊，請參閱 [功能表和 Visual Studio 的命令](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。  
  
 功能表會宣告於.vsct 檔的專案。 如需功能表和.vsct 檔的詳細資訊，請參閱 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 完成這個逐步解說，您可以建立名為功能表 **TestMenu** ，其中包含一個命令。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立 VSIX 專案具有自訂命令的項目範本  
  
1.  建立 VSIX 專案，名為 `TopLevelMenu`。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\#** \/ **擴充性**。  如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  專案開啟時，加入名為的自訂命令項目範本 **TestCommand**。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **自訂命令**。 在 **名稱** 視窗的底部欄位中，將命令檔名稱變更為 **TestCommand.cs**。  
  
## 在 IDE 的功能表列上建立功能表  
  
#### 若要建立功能表  
  
1.  在 **方案總管\] 中**, ，開啟 TestCommandPackage.vsct。  
  
     在檔案結尾，沒有包含數個 \< GuidSymbol \> 節點的 \< 符號 \> 節點。 在名為 guidTestCommandPackageCmdSet 節點中，加入新的符號，如下所示︰  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  \< 群組 \> 之前 \< 命令 \> 節點中建立空的 \< 功能表 \> 節點。 在 \< 功能表 \> 節點中，加入 \< 功能表 \> 節點，如下所示︰  
  
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
  
     `guid` 和 `id` \] 功能表上的值指定的命令集及特定的功能表中的命令集。  
  
     `guid` 和 `id` 父系值放置在 Visual Studio 功能表列，其中包含工具和增益集的功能表中的區段的功能表。  
  
     值 `CommandName` 字串會指定文字的功能表項目中顯示。  
  
3.  在 \< 群組 \> 區段中，找不到 \< 群組 \> 並變更 \< 父 \> 項目，以指向我們剛才加入的功能表︰  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     這可讓 \[新增\] 功能表中群組的一部分。  
  
4.  尋找 `Buttons` 一節。 請注意， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 套件\] 範本產生 `Button` 設為其父代的項目 `MyMenuGroup`。 如此一來，這個命令會出現在功能表上。  
  
## 建置和測試擴充功能  
  
1.  建置此專案並開始偵錯。 實驗執行個體的執行個體應該會出現。  
  
2.  在實驗執行個體的功能表列應該包含 **TestMenu** 功能表。  
  
3.  在 **TestMenu** \] 功能表上，按一下 \[ **叫用測試命令**。  
  
     訊息方塊應該會出現，並顯示訊息 「 第封裝頁，在 TopLevelMenu.TestCommand.MenuItemCallback\(\) TestCommand 」。 這表示，適用於新的命令。  
  
## 請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)