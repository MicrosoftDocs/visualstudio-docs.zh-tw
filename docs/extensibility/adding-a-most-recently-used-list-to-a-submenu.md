---
title: "最近加入的大部分使用子功能表的清單 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MRU 清單"
  - "功能表建立 MRU 清單"
  - "最近使用的"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 46
---
# 最近加入的大部分使用子功能表的清單
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此逐步解說建立於中示範 [將子功能表新增至功能表](../extensibility/adding-a-submenu-to-a-menu.md), ，並示範如何加入子功能表中的動態清單。 動態清單會形成建立最近使用的 \(MRU\) 清單的基礎。  
  
 動態功能表清單開始\] 功能表上的預留位置。 每一次，就會顯示功能表，Visual Studio 整合式的開發環境 \(IDE\) 會要求 VSPackage 應會顯示在 \[版面配置區的所有命令。 動態清單可能\] 功能表上的任何位置。 不過，動態清單通常儲存，並且位於子功能表或功能表底端顯示本身。 藉由使用這些設計模式，您可以啟用動態命令來進行擴大和縮減而不會影響其他命令功能表中的位置清單。 在本逐步解說中，動態 MRU 清單會顯示在現有的子功能表，以換行分隔的子功能表的其餘部分的底部。  
  
 技術上來說，動態清單也可以套用至工具列。 不過，我們不鼓勵這種用法因為工具列應該維持不變，除非使用者採取特定的步驟來變更它。  
  
 此逐步解說會建立四個項目，變更其順序，每次選取其中一種它們 MRU 清單 （選取的項目移至清單頂端）。  
  
 如需功能表和.vsct 檔的詳細資訊，請參閱 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## 建立擴充功能  
  
-   請依照下列中的程序 [將子功能表新增至功能表](../extensibility/adding-a-submenu-to-a-menu.md) 在下列程序中建立已修改的子功能表。  
  
 在本逐步解說的程序會假設 VSPackage 的名稱為 `TopLevelMenu`, ，這是用於名稱 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)。  
  
## 建立動態項目清單的命令  
  
1.  開啟 TestCommandPackage.vsct。  
  
2.  在 `Symbols` 區段的 `GuidSymbol` 節點名為 guidTestCommandPackageCmdSet，新增的符號 `MRUListGroup` 群組和 `cmdidMRUList` 命令，如下所示。  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  在 `Groups` 區段，現有的群組項目之後加入宣告的群組。  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  在 `Buttons` 區段中，新增代表新宣告的命令，在現有的按鈕項目之後的節點。  
  
    ```c#  
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
  
     `DynamicItemStart` 旗標可讓動態產生的命令。  
  
5.  建置專案並啟動偵錯以測試新命令的顯示。  
  
     在 **TestMenu** \] 功能表上，按一下 \[新增子功能表中， **\] 子功能表**, ，以顯示新的命令， **MRU 預留位置**。 動態 MRU 清單的命令會在下一個程序中實作後，這個命令標籤將會由該清單取代每次開啟子功能表。  
  
## 填滿 MRU 清單  
  
1.  在 TestCommandPackageGuids.cs，加入下列幾行中的現有命令識別碼之後 `TestCommandPackageGuids` 類別定義。  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  TestCommand.cs 中新增下列 using 陳述式。  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  最後一個 AddCommand 通話之後，TestCommand 建構函式中加入下列程式碼。`InitMRUMenu` 稍後定義  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  TestCommand 類別中新增下列程式碼。 此程式碼初始化字串，代表要顯示最近使用清單上的項目的清單。  
  
    ```c#  
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
  
5.  之後 `InitializeMRUList` 方法中，加入 `InitMRUMenu` 方法。 這會初始化 MRU 清單功能表命令。  
  
    ```c#  
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
  
     MRU 清單中，您必須建立功能表命令物件的每個可能的項目。 IDE 呼叫 `OnMRUQueryStatus` MRU 清單，直到有更多的項目中各個項目的方法。 在 managed 程式碼，知道有沒有其他項目 IDE 的唯一方式就是先建立所有可能的項目。 如果您想，您可以將標示為不顯示在其他項目第一次使用 `mc.Visible = false;` 建立功能表命令之後。 這些項目便可看到稍後使用 `mc.Visible = true;` 中 `OnMRUQueryStatus` 方法。  
  
6.  之後 `InitMRUMenu` 方法中，新增下列 `OnMRUQueryStatus` 方法。 這是設定為每個最近一次使用項目文字的處理常式。  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  之後 `OnMRUQueryStatus` 方法中，新增下列 `OnMRUExec` 方法。 這是用來選取最近一次使用項目處理常式。 這個方法會將選取的項目移至清單的頂端，並接著在訊息方塊會顯示選取的項目。  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
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
  
## 測試 MRU 清單  
  
#### 若要測試 MRU 功能表清單  
  
1.  建置專案並開始偵錯  
  
2.  在 **TestMenu** \] 功能表上，按一下 \[ **叫用 TestCommand**。 這麼做會顯示訊息方塊，表示已選取命令。  
  
    > [!NOTE]
    >  此步驟，才能強制載入，並正確地顯示 MRU 清單 VSPackage。 如果您略過此步驟中，不會顯示最近使用清單。  
  
3.  在 **測試功能表** \] 功能表上，按一下 \[ **\] 子功能表**。 四個項目清單會顯示子功能表下分隔符號的結尾。 當您按一下 **項目 3**, ，應該會出現訊息方塊，並將其顯示文字、 「 選取項目 3"。 （如果未顯示的四個項目清單，請確定您已經依照先前步驟中的指示。）  
  
4.  開啟子功能表。 請注意， **項目 3** 現在是在清單的頂端和其他項目已被發送向下移動一個位置。 按一下 \[ **項目 3** 一次，請注意，仍會顯示訊息方塊 」 選取項目 3 」，這表示文字已正確地移動到新位置，以及命令標籤。  
  
## 請參閱  
 [以動態方式加入功能表項目](../extensibility/dynamically-adding-menu-items.md)