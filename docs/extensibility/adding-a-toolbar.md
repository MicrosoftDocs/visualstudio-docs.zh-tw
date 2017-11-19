---
title: "新增工具列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da6ea8eac18151f0efbaefb3e9f910b695630669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-toolbar"></a>新增工具列
本逐步解說示範如何將工具列新增至 Visual Studio IDE。  
  
 工具列是包含繫結至命令按鈕的水平或垂直區域。 根據其實作，在 IDE 中的工具列可以重新定位、 停駐在 IDE 主視窗的任何一側或保持在其他視窗的前面。  
  
 此外，使用者可以將命令加入至工具列，或從其中移除使用**自訂** 對話方塊。 一般而言，在 Vspackage 中的工具列是使用者可自訂。 IDE 會處理所有的自訂，VSPackage 回應命令。 VSPackage 不必知道命令實體所在的位置。  
  
 如需功能表的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-toolbar"></a>使用工具列建立擴充功能  
 建立 VSIX 專案，名為`IDEToolbar`。 加入名為的功能表命令項目範本**ToolbarTestCommand**。 如需如何執行這項操作資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Ide 建立工具列  
  
1.  在 ToolbarTestCommandPackage.vsct，尋找符號 > 一節。 在名為 guidToolbarTestCommandPackageCmdSet GuidSymbol 元素中，加入宣告的工具列和工具列群組，如下所示。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  Commands 區段頂端建立功能表區段。 定義工具列的 [功能表] 區段中加入功能表項目。  
  
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
  
     工具列不能巢狀像子功能表。 因此，您沒有指定的父群組。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 一般而言，以程式設計的方式，定義工具列的初始位置，但使用者的後續變更永久變更。  
  
3.  在[群組](../extensibility/groups-element.md) 區段中，在現有的群組項目之後, 定義[群組](../extensibility/group-element.md)包含的工具列命令的項目。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  請在工具列上顯示的按鈕。 在 [按鈕] 區段中，取代父系中的區塊至工具列按鈕。 產生的按鈕區塊應該看起來像這樣：  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     根據預設，如果工具列沒有任何命令，它不會出現。  
  
5.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
6.  以滑鼠右鍵按一下 Visual Studio 功能表列，以取得工具列的清單。 選取**測試工具列**。  
  
7.  您現在應該看到您的工具列右邊的 [檔案] 圖示中尋找圖示。 當您按一下圖示時，您應該會看到訊息方塊，表示**ToolbarTestCommandPackage。內部 IDEToolbar.ToolbarTestCommand.MenuItemCallback()**。  
  
## <a name="see-also"></a>另請參閱  
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)