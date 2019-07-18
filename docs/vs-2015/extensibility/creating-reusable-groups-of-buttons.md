---
title: 建立可重複使用的按鈕群組 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 45
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ac1fd0dc242ae8b8979a3f420f5e1c4d837f62b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405710"
---
# <a name="creating-reusable-groups-of-buttons"></a>建立可重複使用的按鈕群組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

命令群組是一律會出現在一起的功能表或工具列的命令集合。 將它指派給不同的父功能表.vsct 檔的 CommandPlacements 區段中，可以重複使用任何命令群組。  
  
 命令群組通常包含按鈕，但也可以包含其他的功能表或下拉式方塊。  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>若要建立一組可重複使用按鈕  
  
1. 建立 VSIX 專案，名為`ReusableButtons`。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2. 當專案開啟時，新增名為的自訂命令項目範本**ReusableCommand**。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在 **加入新項目**對話方塊中，移至**Visual C# / 擴充性**，然後選取**自訂命令**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為**ReusableCommand.cs**。  
  
3. 在.vsct 檔案中，移至的 Symbols 區段，並尋找 GuidSymbol 項目，其中包含群組和專案的命令。 它應該命名為 guidReusableCommandPackageCmdSet。  
  
4. 新增 IDSymbol 為每個按鈕，您將新增至群組，如下列範例所示。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     根據預設，命令項目範本會建立名為的群組**MyGroup**和按鈕所提供，以及每個 IDSymbol 項目名稱。  
  
5. 在 [群組] 區段中，建立具有指定的 Symbols 區段中的項目相同的 GUID 和 ID 屬性的群組項目。 您也可以使用現有的群組，或使用所提供的命令範本，如下列範例所示的項目。 此群組會出現在**工具**功能表  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>若要建立一組以供重複使用的按鈕  
  
1. 您可以輸入命令或功能表群組中使用群組作為父定義中的命令或功能表上，或藉由使用 CommandPlacements 區段中將命令或功能表放入群組。  
  
     在 [按鈕] 區段中定義具有您的群組，做為其父系的按鈕或使用按鈕所提供的 [套件] 範本中，如下列範例所示。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2. 如果按鈕必須出現在多個群組，請為其建立項目，在 CommandPlacements 區段中，必須放在命令區段之後。 設定 CommandPlacement 元素，以符合您想要的位置，的按鈕的 GUID 和 ID 屬性，然後設定的 GUID 和 ID，其父項目的其中一個目標群組，如下列範例所示。  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    > [優先順序] 欄位的值會決定新的命令群組中的命令位置。 CommandPlacement 元素會覆寫項目定義中設定中，設定優先順序。 具有較高的優先順序值的命令之前，會顯示具有較低的優先順序值的命令。 允許重複的優先順序值，但無法保證有相同的優先順序值的命令的相對位置，因為順序**devenv /setup**命令會從登錄中建立的最後一個介面可能不一致。  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>若要將一組可重複使用按鈕放在功能表上  
  
1. 建立中的項目`CommandPlacements`一節。 設定的 GUID 和 ID 的`CommandPlacement`您的群組，其中的項目和設定的目標位置的父代 GUID 和 ID。  
  
     CommandPlacements 區段應該放置後方命令區段：  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     命令群組可以包含一個以上的功能表中。 在父功能表可以是其中一個您所建立的由所提供的其中一個[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]（如中所述 ShellCmdDef.vsct 或 SharedCmdDef.vsct），或在另一個 VSPackage 中定義的其中一個。 父圖層數目沒有限制，只要在父功能表最終會連線到[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]或 VSPackage 所顯示的捷徑功能表。  
  
     下列範例會將群組放**方案總管 中**工具列右邊的 其他 按鈕。  
  
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
