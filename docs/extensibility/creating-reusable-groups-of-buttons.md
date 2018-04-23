---
title: 建立可重複使用的按鈕群組 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97ee7cc2ec63a94036472ccce07b1dc9fa736504
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-reusable-groups-of-buttons"></a>建立可重複使用的按鈕群組
命令群組是一律會出現在一起的功能表或工具列的命令集合。 任何命令群組可以藉由指派至不同的父功能表.vsct 檔的 CommandPlacements 區段中重複使用。  
  
 命令群組通常包含按鈕，但是也可以包含其他功能表或下拉式方塊。  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>若要建立一組可重複使用按鈕  
  
1.  建立 VSIX 專案，名為`ReusableButtons`。 如需詳細資訊，請參閱[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  當專案開啟時，加入名為的自訂命令項目範本**ReusableCommand**。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**自訂命令**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**ReusableCommand.cs**。  
  
3.  在.vsct 檔案中，移至 [符號] 區段，並尋找 GuidSymbol 項目，其中包含群組和專案的命令。 其應為 guidReusableCommandPackageCmdSet。  
  
4.  新增 IDSymbol 為每個按鈕，您將新增至群組，如下列範例所示。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     根據預設，命令項目範本建立名為群組**MyMenuGroup**和按鈕所提供，以及每個 IDSymbol 項目名稱。  
  
5.  在 [群組] 區段中，建立具有相同的 GUID 和 ID 屬性為 [符號] 區段中指定的項目組成群組元素。 您也可以使用現有的群組，或使用命令範本，如下列範例所提供的項目。 此群組會出現在**工具**功能表  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>若要建立一組按鈕，以供重複使用  
  
1.  您可以將命令或功能表群組中使用群組當做父代的命令或功能表上，定義中或使用 CommandPlacements > 一節中將命令或功能表放在群組中。  
  
     [按鈕] 區段中定義您的群組，做為其父系，按鈕或使用按鈕所提供的 「 套件 」 範本，如下列範例所示。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  如果按鈕必須出現在多個群組，建立一個項目在 CommandPlacements 區段中，必須放在命令區段之後。 設定以符合您要放置的按鈕 CommandPlacement 項目的 GUID 和 ID 屬性，然後設定的 GUID 和其父項目的 ID 之目標群組，如下列範例所示。  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  [優先順序] 欄位的值會決定新的命令群組中的命令位置。 元素會覆寫設定項目定義 CommandPlacement 中設定的優先權。 具有較高優先順序值的命令之前，會顯示具有較低的優先順序值的命令。 允許重複的優先順序值，但是因為無法保證其相對位置的命令，具有相同的優先順序值的順序**devenv /setup**命令會從登錄中建立的最後一個介面可能不一致。  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>將一組可重複使用按鈕功能表上  
  
1.  在建立項目`CommandPlacements`> 一節。 設定的 GUID 和 ID`CommandPlacement`項目與您的群組，並設定目標位置之父 GUID 和 ID。  
  
     只在 Commands 區段之後應放 CommandPlacements 區段：  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     命令群組可以包含一個以上的功能表上。 在父功能表可以是其中一個您所建立，由所提供的其中一個[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]（如中所述 ShellCmdDef.vsct 或 SharedCmdDef.vsct），或在另一個 VSPackage 中定義的其中一個。 父代層的數目沒有限制，只要在父功能表最後連接到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或加入 VSPackage 所顯示的捷徑功能表。  
  
     下列範例會將群組放**方案總管 中**工具列中，右邊的 其他 按鈕。  
  
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
