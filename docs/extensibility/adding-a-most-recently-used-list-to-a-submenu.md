---
title: 將最近使用的清單添加到子選單 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740296"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>將最近使用的清單加入子選單
本演練基於[將子功能表添加到功能表](../extensibility/adding-a-submenu-to-a-menu.md)中的演示,並演示如何向子功能表添加動態清單。 動態清單構成創建最近使用 (MRU) 列表的基礎。

動態功能表清單以功能表上的占位符開頭。 每次顯示功能表時,Visual Studio 整合式開發環境 (IDE) 都會向 VSPackage 詢問應在占位符處顯示的所有命令。 動態清單可能發生在功能表上的任意位置。 但是,動態清單通常由自身存儲在子菜單或功能表底部。 通過使用這些設計模式,您可以啟用命令的動態列表來展開和收縮,而不會影響功能表上其他命令的位置。 在本演練中,動態 MRU 清單顯示在現有子功能表的底部,由一行與子菜單的其餘部分分開。

從技術上講,動態清單也可以應用於工具列。 但是,我們阻止使用該工具列,因為工具列應保持不變,除非使用者採取特定步驟來更改它。

本演練創建一個 MRU 清單,其中四個專案在每次選擇其中一個專案時都會更改其順序(所選項移動到列表頂部)。

關於選單與 *.vsct*檔案的詳細資訊,請參閱[命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>Prerequisites
若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

## <a name="create-an-extension"></a>建立延伸模組

- 按照將[子功能表添加到菜單](../extensibility/adding-a-submenu-to-a-menu.md)中的過程來創建在以下過程中修改的子功能表。

  本演練中的過程假定 VSPackage 的`TopLevelMenu`名稱為 ,這是在[將菜單添加到 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)中使用的名稱。

## <a name="create-a-dynamic-item-list-command"></a>建立動態項目清單指令

1. 開啟*測試指令套件.vsct*.

2. 在名為`Symbols`guidTestCommandPackageCmdSet`GuidSymbol`的 節點`MRUListGroup`中,添加`cmdidMRUList`組和命令的 符號,如下所示。

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. 在節中`Groups`,在現有組條目之後添加聲明的組。

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. 在節中`Buttons`,在現有按鈕條目之後添加一個節點以表示新聲明的命令。

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

    該`DynamicItemStart`標誌允許動態生成命令。

5. 生成專案並開始調試以測試新命令的顯示。

    在 **「測試選單」** 選單上,按下新的子選單「**子選單**」 以顯示新命令**MRU 占位元**。 在下一個過程中實現命令的動態 MRU 清單後,每次打開子功能表時,此命令標籤都將替換為該清單。

## <a name="filling-the-mru-list"></a>填寫 MRU 清單

1. 在*TestCommandPackageGuids.cs*中,在`TestCommandPackageGuids`類定義中的現有命令指示后添加以下行。

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. 在*TestCommand.cs*添加以下 using 語句。

    ```csharp
    using System.Collections;
    ```

3. 在上次 AddCommand 調用之後的 TestCommand 建構函數中添加以下代碼。 稍後會`InitMRUMenu`定義

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. 在 TestCommand 類中添加以下代碼。 此代碼初始化表示要在 MRU 清單中顯示的項的字串清單。

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

5. 在`InitializeMRUList`方法之後,添加`InitMRUMenu`方法。 這將初始化 MRU 清單功能表命令。

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

    您必須為 MRU 清單中的每個可能項創建功能表命令物件。 IDE 調`OnMRUQueryStatus`用 MRU 清單中每個項的方法,直到沒有更多項。 在託管代碼中,IDE 知道沒有更多項的唯一方法是首先創建所有可能的專案。 如果需要,可以在創建菜單命令后使用`mc.Visible = false;`,將其他項標記為最初不可見。 然後,可以使用`mc.Visible = true;``OnMRUQueryStatus`方法稍後使這些項目可見。

6. 在`InitMRUMenu`方法之後,添加以下`OnMRUQueryStatus`方法。 這是為每個 MRU 項設置文本的處理程式。

    ```csharp
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

7. 在`OnMRUQueryStatus`方法之後,添加以下`OnMRUExec`方法。 這是用於選擇 MRU 項的處理程式。 此方法將所選項移動到清單頂部,然後在消息框中顯示所選項。

    ```csharp
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

## <a name="testing-the-mru-list"></a>測試 MRU 清單

1. 建置此專案並開始偵錯。

2. 在**測試功能表選**單上,按下 **「調用測試命令**」。 執行此操作將顯示一個消息框,指示該命令已選定。

    > [!NOTE]
    > 此步驟需要強制 VSPackage 載入並正確顯示 MRU 清單。 如果跳過此步驟,將不會顯示 MRU 清單。

3. 在**測試功能表「功能表上**,按下 **」子功能表**。 四個項目的清單顯示在子菜單的末尾,位於分隔符下方。 按一下專案**3**時,應顯示一個訊息框並顯示文本 **「選定專案 3」。。** (如果未顯示四個項目的清單,請確保已遵循前面的步驟中的說明。

4. 再次打開子功能表。 請注意,**專案 3**現在位於列表的頂部,其他專案已向下推一個位置。 再次按下**專案 3**並注意到訊息框仍顯示 **「選定專案 3」,** 表示文本與命令標籤一起正確移動到新位置。

## <a name="see-also"></a>另請參閱
- [動態新增選單項目](../extensibility/dynamically-adding-menu-items.md)
