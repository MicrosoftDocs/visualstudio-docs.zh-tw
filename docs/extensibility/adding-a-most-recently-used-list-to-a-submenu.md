---
title: 新增 最近使用的子功能表清單 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 462f59d472c6de8872394b2eadd5f33aa27bccca
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710080"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>新增 最近使用的子功能表清單
本逐步解說是根據在示範[子功能表加入至功能表](../extensibility/adding-a-submenu-to-a-menu.md)，並示範如何加入子功能表中的動態清單。 動態清單構成建立最近使用的 (MRU) 清單的基礎。

動態功能表清單開始功能表上的預留位置。 每一次，就會顯示功能表，Visual Studio 整合式的開發環境 (IDE) 會要求應該在將預留位置顯示的所有命令的 VSPackage。 動態清單可以出現在功能表上的任何位置。 不過，動態清單會通常儲存，並顯示自己本身全部放在子功能表上，或在功能表的底端。 藉由使用這些設計模式，您可以啟用動態清單的命令來進行擴大和縮減而不會影響其他命令功能表上的位置。 在此逐步解說中，動態的 MRU 清單會顯示在現有的子功能表，以換行分隔的子功能表的其餘部分的底部。

技術上來說，動態清單也可以套用至工具列。 不過，我們鼓勵使用量，因為工具列應該保持不變，除非使用者採取特定步驟，來變更它。

此逐步解說會建立四個項目變更其順序，每次在於其中已選取的 MRU 清單 （選取的項目移至清單頂端）。

如需功能表和 *.vsct*檔，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>必要條件
若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

## <a name="create-an-extension"></a>建立擴充功能

- 請依照下列中的程序[子功能表加入功能表](../extensibility/adding-a-submenu-to-a-menu.md)下列程序中建立的已修改的子功能表。

  在本逐步解說的程序會假設 VSPackage 的名稱是`TopLevelMenu`，這是名稱中使用[Visual Studio 功能表列中加入功能表](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)。

## <a name="create-a-dynamic-item-list-command"></a>建立動態項目清單命令

1. 開啟*TestCommandPackage.vsct*。

2. 在`Symbols`區段中`GuidSymbol`節點中名為 guidTestCommandPackageCmdSet，新增的符號`MRUListGroup`群組和`cmdidMRUList`命令，如下所示。

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. 在 `Groups`區段中，現有的群組項目之後加入宣告的群組。

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. 在 `Buttons`區段中，新增一個節點，代表新宣告的命令，在現有的按鈕項目之後。

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

    `DynamicItemStart`旗標可啟用動態產生的命令。

5. 建置專案，並開始偵錯來測試新的命令的顯示。

    上**TestMenu**功能表上，按一下 新的子功能表中，**子功能表**，以顯示新的命令**MRU 預留位置**。 在下一個程序中實作命令的動態 MRU 清單之後，此命令標籤將被取代該清單的每次開啟子功能表。

## <a name="filling-the-mru-list"></a>填滿 MRU 清單

1. 在  *TestCommandPackageGuids.cs*，在現有的命令識別碼之後加入下列幾行`TestCommandPackageGuids`類別定義。

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. 在  *TestCommand.cs*新增下列 using 陳述式。

    ```csharp
    using System.Collections;
    ```

3. 最後一個 AddCommand 呼叫之後，TestCommand 建構函式中加入下列程式碼。 `InitMRUMenu`稍後定義

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. TestCommand 類別中新增下列程式碼。 此程式碼會初始化字串表示，MRU 清單上顯示的項目的清單。

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

5. 在後`InitializeMRUList`方法中，新增`InitMRUMenu`方法。 這會初始化 MRU 清單功能表命令。

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

    MRU 清單中，您必須建立功能表命令物件的每個可能的項目。 IDE 呼叫`OnMRUQueryStatus`MRU 清單，直到沒有更多的項目中的每個項目的方法。 在 managed 程式碼，知道有沒有更多的項目 ide 的唯一方式是先建立所有可能的項目。 如果您想，您可以將標記為不顯示在其他項目第一次使用`mc.Visible = false;`建立功能表命令之後。 這些項目便可看到稍後透過`mc.Visible = true;`在`OnMRUQueryStatus`方法。

6. 在後`InitMRUMenu`方法中，新增下列`OnMRUQueryStatus`方法。 這是設定每個 MRU 項目文字的處理常式。

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

7. 在後`OnMRUQueryStatus`方法中，新增下列`OnMRUExec`方法。 這是選取最近使用項目處理常式。 這個方法會將選取的項目移至清單頂端，然後顯示訊息方塊中的 選取的項目。

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

2. 在  **TestMenu**功能表上，按一下**叫用 TestCommand**。 如此一來，就會顯示訊息方塊，指出命令已選取。

    > [!NOTE]
    > 此步驟，才能強制載入，並正確地顯示 MRU 清單 VSPackage。 如果您略過此步驟中，MRU 清單將不會顯示。

3. 在上 **[測試] 功能表**功能表上，按一下**子功能表**。 四個項目清單會顯示子功能表中，以下為分隔符號的結尾。 當您按一下 **項目 3**，應該會出現訊息方塊，並將其顯示的文字**選取項目 3**。 （如果未顯示四個項目清單，請確定您已遵循先前步驟中的指示。）

4. 再次開啟子功能表。 請注意，**項目 3**現在位於清單頂端和其他項目已推送向下移動一個位置。 按一下 **項目 3**一次，請注意，仍會顯示訊息方塊**選取項目 3**，表示文字是否已正確地移到新位置，以及命令的標籤。

## <a name="see-also"></a>另請參閱
- [以動態方式加入功能表項目](../extensibility/dynamically-adding-menu-items.md)
