---
title: 將最近使用的清單新增至子功能表 |Microsoft Docs
description: 瞭解如何將包含最近使用之功能表命令的動態清單新增至 Visual Studio 整合式開發環境 (IDE) 中的子功能表。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb238afb0f583f1b913fbd87f4f50e43679ebd7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060012"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>將最近使用的清單新增至子功能表
本逐步解說是以在 [功能表中加入子功能表](../extensibility/adding-a-submenu-to-a-menu.md)的示範為基礎，並示範如何將動態清單新增至子功能表。 動態清單會形成建立最近使用之 (MRU) 清單的基礎。

動態功能表清單會以功能表上的預留位置開頭。 每次顯示功能表時，Visual Studio 的整合式開發環境 (IDE) 會要求 VSPackage 所有應顯示在預留位置的命令。 動態清單可以出現在功能表上的任何位置。 不過，動態清單通常會在子功能表或功能表底部儲存並顯示。 藉由使用這些設計模式，您可以啟用命令的動態清單來展開和收縮，而不會影響功能表上其他命令的位置。 在這個逐步解說中，動態 MRU 清單會顯示在現有子功能表的底部，並以線條的其餘部分分隔。

技術上來說，動態清單也可以套用至工具列。 不過，我們不建議使用，因為工具列應該保持不變，除非使用者採取特定的步驟來變更它。

本逐步解說會建立四個專案的 MRU 清單，這些專案會在每次選取其中一個專案時變更其順序 (選取的專案會移至清單) 的頂端。

如需功能表和 *.vsct* 檔案的詳細資訊，請參閱 [命令、功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="prerequisites"></a>必要條件
若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

## <a name="create-an-extension"></a>建立延伸模組

- 遵循將子功能表 [加入功能表](../extensibility/adding-a-submenu-to-a-menu.md) 中的程式，以建立在下列程式中修改的子功能表。

  本逐步解說中的程式假設 VSPackage 的名稱是，也 `TestCommand` 就是 [將功能表加入 Visual Studio 的功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)中所使用的名稱。

## <a name="create-a-dynamic-item-list-command"></a>建立動態專案清單命令

1. 開啟 *TestCommandPackage. .vsct*。

2. 在 `Symbols` 區段中，在 `GuidSymbol` 名為 guidTestCommandPackageCmdSet 的節點中，新增 `MRUListGroup` 群組和命令的符號 `cmdidMRUList` ，如下所示。

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. 在 `Groups` 區段中，在現有的群組專案之後加入宣告的群組。

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. 在 `Buttons` 區段中，新增節點以代表新宣告的命令（在現有的按鈕專案之後）。

    ```xml
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

    旗標可 `DynamicItemStart` 讓您以動態方式產生命令。

5. 建立專案並開始進行偵錯工具，以測試新命令的顯示。

    在 [ **TestMenu** ] 功能表上，按一下 [新增子功能表] **子功能表**，以顯示新的命令 **MRU 預留位置**。 在下一個程式中執行動態 MRU 清單命令之後，每次開啟子功能表時，此命令標籤就會由該清單取代。

## <a name="filling-the-mru-list"></a>填入 MRU 清單

1. 在 *TestCommandPackageGuids* 中，將下列幾行加入至類別定義中現有的命令識別碼之後 `TestCommandPackageGuids` 。

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. 在 *TestCommand* 中，新增下列 using 語句。

    ```csharp
    using System.Collections;
    ```

3. 在 TestCommand 的函式中，于最後一個 AddCommand 呼叫之後加入下列程式碼。 `InitMRUMenu`稍後會定義。

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. 在 TestCommand 類別中加入下列程式碼。 此程式碼會初始化字串清單，這些字串表示要在 MRU 清單上顯示的專案。

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

5. 在 `InitializeMRUList` 方法之後，加入 `InitMRUMenu` 方法。 這會初始化 MRU 清單功能表命令。

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

    您必須針對 MRU 清單中的每個可能專案建立功能表命令物件。 IDE `OnMRUQueryStatus` 會針對 MRU 清單中的每個專案呼叫方法，直到沒有其他專案為止。 在 managed 程式碼中，IDE 的唯一方法就是要先建立所有可能的專案，才能知道沒有其他專案。 如果您想要的話，您可以在 `mc.Visible = false;` 建立功能表命令之後，先使用，將其他專案標示為不可見。 之後，您可以在方法中使用來顯示這些專案 `mc.Visible = true;` `OnMRUQueryStatus` 。

6. 在 `InitMRUMenu` 方法之後，加入下列 `OnMRUQueryStatus` 方法。 此處理程式會設定每個 MRU 專案的文字。

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

7. 在 `OnMRUQueryStatus` 方法之後，加入下列 `OnMRUExec` 方法。 這是用來選取 MRU 專案的處理常式。 這個方法會將選取的專案移至清單頂端，然後將選取的專案顯示在訊息方塊中。

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

1. 建置此專案並開始偵錯。

2. 在 [ **TestMenu** ] 功能表上，按一下 [叫用 **TestCommand**]。 這麼做會顯示一個訊息方塊，指出已選取該命令。

    > [!NOTE]
    > 需要執行此步驟，才能強制 VSPackage 載入並正確顯示 MRU 清單。 如果您略過此步驟，則不會顯示 MRU 清單。

3. 在 [ **測試] 功能表** 功能表上，按一下 [ **子功能表**]。 四個專案的清單會顯示在子功能表結尾的分隔符號底下。 當您按一下 [ **專案 3**] 時，應該會出現訊息方塊，並顯示 [ **選取的專案 3**] 文字。  (如果未顯示四個專案的清單，請確定您已遵循先前步驟中的指示。 ) 

4. 再次開啟子功能表。 請注意， **專案 3** 現在位於清單頂端，而其他專案則會被向下推送一個位置。 再次按一下 [ **專案 3** ]，請注意，訊息方塊仍會顯示 **選取的專案 3**，這表示文字已正確地移至新的位置，以及命令標籤。

## <a name="see-also"></a>另請參閱
- [以動態方式加入功能表項目](../extensibility/dynamically-adding-menu-items.md)
