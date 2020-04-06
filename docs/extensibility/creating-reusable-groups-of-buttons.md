---
title: 建立可重用的按鍵群組 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739472"
---
# <a name="create-reusable-groups-of-buttons"></a>建立可重用的按鈕群組
命令組是始終一起出現在功能表或工具列上的命令的集合。 任何命令組都可以通過將它分配給 *.vsct*檔案的命令放置部分中的不同父功能表來重新使用。

 命令組通常包含按鈕,但它們也可以包含其他功能表或組合框。

## <a name="to-create-a-reusable-group-of-buttons"></a>建立可重用的按鈕群組

1. 創建名為的`ReusableButtons`VSIX 專案。 關於詳細資訊,請參閱[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

2. 打開專案時,添加名為 **「可重用命令」的**自定義命令項範本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在「**新增新項目」** 對話框中,轉到**可視化 C#** > **擴充性**並選擇 **「自訂命令**」。 在視窗底部的**名稱「 欄**位中」,將指令檔名變更為*ReusableCommand.cs*。

3. 在 *.vsct*檔中,轉到"符號"部分,並找到包含專案的組和命令的 GuidSymbol 元素。 它應該被命名為 guid 可重用命令包 CmdSet。

4. 為要添加到組的每個按鈕添加 IDSymbol,如以下範例所示。

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     預設情況下,命令項範本將創建名為**MyMenuGroup 的**組和一個包含您提供的名稱的按鈕,以及每個項的 IDSymbol 項目。

5. 在「組」部分中,創建與「符號」部分中給出的屬性相同的 GUID 和 ID 元素的組元素。 您還可以使用現有組,或使用命令範本提供的條目,如以下範例所示。 此組顯示在 **「工具」** 選單上

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>建立按鈕以供重用

1. 可以將命令或功能表放在組中,或者在命令或功能表的定義中將組作為父項,或者通過使用"命令放置"部分將命令或功能表放入組中。

     在"按鈕"部分中,定義一個按鈕,該按鈕以組為父組,或使用包範本提供的按鈕,如以下示例所示。

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. 如果按鈕必須出現在多個組中,請為其在"命令放置"部分創建一個條目,該條目必須放在"命令"部分之後。 將命令放置元素的 GUID 和 ID 屬性設定為與要定位的按鈕的屬性匹配,然後將其父元素的 GUID 和 ID 設定為目標組的 GUID 和 ID,如以下範例所示。

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > "優先權"欄位的值確定命令在新命令組中的位置。 在命令放置元素中設置的優先順序將覆蓋項定義中設置的優先順序。 優先順序較低的命令顯示在具有較高優先順序值的命令之前。 允許重複的優先順序值,但無法保證具有相同優先順序值的命令的相對位置,因為**devenv /setup**命令從註冊表創建最終介面的順序可能不一致。

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>在選單上放置一組可重複使用的按鈕

1. 在`CommandPlacements`節中創建條目。 將元素的`CommandPlacement`GUID 和 ID 設定為組的 GUID 和 ID,並將父 GUID 和 ID 設定為目標位置的 ID。

    命令放置部分應在「命令」部分之後放置:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    命令組可以包含在多個功能表上。 父功能表可以是您創建的功能表,由提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)](如*ShellCmdDef.vsct*或*SharedCmdDef.vsct*中所述),也可以是在另一個 VSPackage 中定義的功能表。 只要父選單最終連接到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage 顯示的快捷功能表或快捷功能表,父級圖層的數量是無限的。

    下面的範例將組放在**解決方案資源管理員**工具列上,位於其他按鈕的右側。

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
