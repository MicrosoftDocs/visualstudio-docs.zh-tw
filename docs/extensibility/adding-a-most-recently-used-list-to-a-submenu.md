---
title: "加入 最近使用的子功能表清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: "46"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d622bd917548666e12eff6d29639f62d3ef4bc1f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>最近加入的大部分用到子功能表清單
本逐步解說是根據在示範[加入功能表的子功能表](../extensibility/adding-a-submenu-to-a-menu.md)，並示範如何加入子功能表中的動態清單。 動態清單構成建立最近使用的 (MRU) 清單的基礎。  
  
 動態功能表清單從開始功能表上的預留位置。 每一次，就會顯示功能表，Visual Studio 整合式的開發環境 (IDE) 會要求所有命令應該會顯示在預留位置的 VSPackage。 動態清單可能功能表上的任何位置。 不過，動態清單通常會儲存並顯示自己本身全部放在子功能表或功能表底端。 藉由使用這些設計模式，您可以啟用動態清單的命令，以展開和收縮，而不會影響其他功能表命令的位置。 在本逐步解說中，動態 MRU 清單會顯示一條線從子功能表的其餘部分隔開現有子功能表的底部。  
  
 技術上來說，動態清單也可以套用至工具列。 不過，我們不鼓勵這種用法因為工具列應該維持不變，除非使用者採取特定的步驟來變更它。  
  
 這個逐步解說會建立四個項目變更其順序，每次選取的其中一個這些 MRU 清單 （選取的項目將移至清單頂端）。  
  
 如需功能表和.vsct 檔案的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="creating-an-extension"></a>建立擴充功能  
  
-   請依照下列中的程序[加入功能表的子功能表](../extensibility/adding-a-submenu-to-a-menu.md)在下列程序中建立已修改的子功能表。  
  
 在本逐步解說的程序假設 VSPackage 的名稱是`TopLevelMenu`，這是使用中的名稱[功能表加入 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)。  
  
## <a name="creating-a-dynamic-item-list-command"></a>建立動態項目清單的命令  
  
1.  開啟 TestCommandPackage.vsct。  
  
2.  在`Symbols`區段的`GuidSymbol`節點名為 guidTestCommandPackageCmdSet，新增的符號`MRUListGroup`群組和`cmdidMRUList`命令，如下所示。  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  在`Groups`區段中，現有的群組項目後面加入宣告的群組。  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  在`Buttons`區段中，新增代表新宣告的命令，在現有的按鈕項目之後的節點。  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart`旗標可讓要動態產生的命令。  
  
5.  建置專案並開始偵錯測試新命令的顯示。  
  
     上**TestMenu**功能表上，按一下 新增 子功能表** 子功能表**，以顯示新的命令**MRU 預留位置**。 實作命令的動態 MRU 清單中下一個程序之後，此命令標籤將被取代該清單所每次開啟子功能表。  
  
## <a name="filling-the-mru-list"></a>填滿 MRU 清單  
  
1.  在 TestCommandPackageGuids.cs，加入下列行中的現有命令識別碼之後`TestCommandPackageGuids`類別定義。  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  在 TestCommand.cs 加入下列 using 陳述式。  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  TestCommand 建構函式中加入下列程式碼，最後一個 AddCommand 呼叫之後。 `InitMRUMenu`稍後將會定義  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand 類別中加入下列程式碼。 這個程式碼初始化字串，代表要顯示最近使用清單上的項目的清單。  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  之後`InitializeMRUList`方法，加入`InitMRUMenu`方法。 這會初始化 MRU 清單功能表命令。  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     MRU 清單中，您必須建立功能表命令物件的每個可能的項目。 IDE 呼叫`OnMRUQueryStatus`MRU 清單，直到沒有其他項目中的每個項目的方法。 在 managed 程式碼，要知道有沒有更多的項目 ide 的唯一方式是先建立所有可能的項目。 如果您想，您可以將標記為不顯示在其他項目第一次使用`mc.Visible = false;`建立功能表命令之後。 這些項目然後可變成可見稍後使用`mc.Visible = true;`中`OnMRUQueryStatus`方法。  
  
6.  之後`InitMRUMenu`方法，加入下列`OnMRUQueryStatus`方法。 這是設定為每個 MRU 項目文字的處理常式。  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  之後`OnMRUQueryStatus`方法，加入下列`OnMRUExec`方法。 這是選取 MRU 項目處理常式。 這個方法會將選取的項目移至清單頂端，然後在訊息方塊中顯示選取的項目。  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>測試 MRU 清單  
  
#### <a name="to-test-the-mru-menu-list"></a>若要測試 MRU 功能表清單  
  
1.  建置專案並開始偵錯  
  
2.  在**TestMenu**功能表上，按一下 **叫用 TestCommand**。 這麼做會顯示訊息方塊，表示已選取命令。  
  
    > [!NOTE]
    >  此步驟，才能強制載入並正確地顯示 MRU 清單 VSPackage。 如果您略過此步驟中，不會顯示最近使用清單。  
  
3.  在**測試功能表**功能表上，按一下 [ **] 子功能表**。 四個項目清單會顯示子功能表下方分隔符號的結尾。 當您按一下**項目 3**，應該會出現訊息方塊，並將其顯示文字，也就是 「 選取項目 3 」。 （如果未顯示的四個項目清單，請確定，您已依照先前步驟中的指示。）  
  
4.  再次開啟子功能表。 請注意，**項目 3**現在位於清單頂端和其他項目已推入向下移動一個位置。 按一下**項目 3**一次，並注意，訊息方塊仍然會顯示 「 選取項目 3 」，表示文字都已正確地移到新位置，以及命令標籤。  
  
## <a name="see-also"></a>另請參閱  
 [以動態方式加入功能表項目](../extensibility/dynamically-adding-menu-items.md)