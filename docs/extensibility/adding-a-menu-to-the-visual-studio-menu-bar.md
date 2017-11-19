---
title: "將功能表加入至 Visual Studio 功能表列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: "51"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e4a2485b7e702844a037787234ef3a1ab66495d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>將功能表加入至 Visual Studio 功能表列
本逐步解說示範如何將功能表加入 Visual Studio 整合式的開發環境 (IDE) 的功能表列。 IDE 的功能表列包含功能表類別，例如**檔案**，**編輯**，**檢視**，**視窗**，和**協助**.  
  
 之前的 Visual Studio 功能表列中加入新的功能表，請考慮您的命令是否應該置於現有的功能表。 如需命令位置的詳細資訊，請參閱[功能表和命令適用於 Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)。  
  
 功能表會宣告.vsct 檔案中的專案。 如需功能表和.vsct 檔案的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 完成這個逐步解說，您可以建立名為功能表**TestMenu** ，其中包含一個命令。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>建立 VSIX 專案具有自訂命令項目範本  
  
1.  建立 VSIX 專案，名為`TopLevelMenu`。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C#** / **擴充性**。  如需詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  當專案開啟時，加入名為的自訂命令項目範本**TestCommand**。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**TestCommand.cs**。  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>在 IDE 的功能表列上建立功能表  
  
#### <a name="to-create-a-menu"></a>建立功能表  
  
1.  在**方案總管 中**，開啟 TestCommandPackage.vsct。  
  
     在檔案結尾，沒有\<符號 > 節點，節點包含數個\<GuidSymbol > 節點。 在名為 guidTestCommandPackageCmdSet 節點中，加入新的符號，如下所示：  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  建立空白\<功能表 > 節點中的\<命令 > 節點，之前\<群組 >。 在\<功能表 > 節點，加入\<功能表 > 節點，如下所示：  
  
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
  
     `guid`和`id`功能表的值指定命令集及特定的功能表命令集。  
  
     `guid`和`id`父系值放置功能表，在 Visual Studio 功能表列，其中包含工具和增益集的功能表中的區段。  
  
     值`CommandName`字串會指定文字應該出現在功能表項目。  
  
3.  在\<群組 > 區段中，尋找\<群組 >，並變更\<父 > 以指向剛才加入的功能表項目：  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     這可讓新的功能表中群組的一部分。  
  
4.  尋找`Buttons`> 一節。 請注意，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已產生封裝範本`Button`設為其父代的項目`MyMenuGroup`。 如此一來，此命令會顯示在您的功能表。  
  
## <a name="building-and-testing-the-extension"></a>建置和測試擴充功能  
  
1.  建置此專案並開始偵錯。 實驗執行個體的執行個體應該會出現。  
  
2.  在實驗執行個體的功能表列應該包含**TestMenu**功能表。  
  
3.  在**TestMenu**功能表上，按一下 **叫用測試命令**。  
  
     訊息方塊應該會出現並顯示 「 第封裝頁，內部 TopLevelMenu.TestCommand.MenuItemCallback() TestCommand 」 的訊息。 這表示，適用於新的命令。  
  
## <a name="see-also"></a>另請參閱  
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)