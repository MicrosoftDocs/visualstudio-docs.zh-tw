---
title: 建立可重複使用的按鈕群組 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 477014ed77b60821ad191ba6842999be6f528fee
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903646"
---
# <a name="create-reusable-groups-of-buttons"></a>建立可重複使用的按鈕群組
「命令群組」是一種命令集合，一律會出現在功能表或工具列上。 任何命令群組都可以重複使用，方法是在 *.vsct*檔案的 CommandPlacements 區段中，將它指派給不同的父功能表。

 命令群組通常包含按鈕，但也可以包含其他功能表或下拉式方塊。

## <a name="to-create-a-reusable-group-of-buttons"></a>建立可重複使用的按鈕群組

1. 建立名為的 VSIX 專案 `ReusableButtons` 。 如需詳細資訊，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

2. 當專案開啟時，新增名為**ReusableCommand**的自訂命令專案範本。 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**新增專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  **Extensibility**然後選取 [**自訂命令**]。 在視窗底部的 [**名稱**] 欄位中，將命令檔名稱變更為*ReusableCommand.cs*。

3. 在 *.vsct*檔案中，移至 [符號] 區段，然後尋找包含專案之群組和命令的 GuidSymbol 元素。 它應該命名為 guidReusableCommandPackageCmdSet。

4. 為您將新增至群組的每個按鈕新增 IDSymbol，如下列範例所示。

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     根據預設，命令專案範本會建立名為**MyMenuGroup**的群組，以及一個具有您所提供名稱的按鈕，以及每個的 IDSymbol 專案。

5. 在 [群組] 區段中，建立具有與 [符號] 區段中指定之 GUID 和 ID 屬性相同的群組元素。 您也可以使用現有的群組，或使用命令範本所提供的專案，如下列範例所示。 這個群組會出現在 [**工具**] 功能表上

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>建立要重複使用的按鈕群組

1. 您可以使用群組做為命令或功能表定義中的父系，或使用 [CommandPlacements] 區段將命令或功能表放在群組中，將命令或功能表放在群組中。

     在 [按鈕] 區段中，定義具有您的群組做為其父系的按鈕，或使用由封裝範本提供的按鈕，如下列範例所示。

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. 如果按鈕必須出現在多個群組中，請在 [CommandPlacements] 區段中為其建立專案，這必須置於 [命令] 區段後面。 設定 CommandPlacement 元素的 GUID 和 ID 屬性，以符合您想要放置的按鈕，然後將其父元素的 GUID 和 ID 設定為目標群組的識別碼，如下列範例所示。

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > [優先順序] 欄位的值會決定命令在新命令群組中的位置。 在 CommandPlacement 元素中設定的優先順序會覆寫專案定義中的集合。 具有較低優先順序值的命令會顯示在具有較高優先順序值的命令之前。 允許重複的優先順序值，但具有相同優先順序值之命令的相對位置無法保證，因為**devenv/setup**命令從登錄建立最終介面的順序可能不一致。

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>若要在功能表上放置可重複使用的按鈕群組

1. 在區段中建立專案 `CommandPlacements` 。 將元素的 GUID 和 ID 設定 `CommandPlacement` 為群組的識別碼，並將父 GUID 和 id 設定為目標位置的識別碼。

    CommandPlacements 區段應該放在命令區段之後：

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    一個命令群組可以包含在一個以上的功能表上。 父功能表可以是您所建立的其中一個 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] （如*ShellCmdDef. .Vsct*或*SharedCmdDef*中所述），或是另一個 VSPackage 中定義的功能表。 只要父功能表最後連線到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 VSPackage 所顯示的快捷方式功能表，父系層的數目就不受限制。

    下列範例會將群組放在 [**方案總管**] 工具列上的 [其他] 按鈕右邊。

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
