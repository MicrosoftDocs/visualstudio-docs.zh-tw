---
title: MenuCommand 對比OleMenuCommands |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: jillfra
ms.openlocfilehash: 42c471ca924bfded62db32a956a26c07240459eb
ms.sourcegitcommit: 3cc73e74921a9ceb622542e0e263abeebc455c00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2019
ms.locfileid: "67624462"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommand 對比OleMenuCommand
您可以藉由衍生自建立功能表命令<xref:System.ComponentModel.Design.MenuCommand>或從<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>物件，並實作適當的事件處理常式。 在大多數情況下，您可以使用 <xref:System.ComponentModel.Design.MenuCommand>，就如同 VSPackage 專案範本一樣，但有時候您可能需要使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>。  
  
 VSPackage 會提供給 IDE 的命令必須顯示並啟用，使用者才能使用它們。 使用 Visual Studio Package 專案範本建立在 .vsct 檔案中建立命令，它們預設會顯示並啟用。 設定一些命令旗標，例如 `DynamicItemStart`，可以變更預設行為。 可見性、啟用的狀態，以及命令的其他屬性，也可以在執行階段的程式碼中藉由存取與命令相關聯的 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 物件來變更。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱 < [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Visual Studio Package 範本的範本位置  
 您可以在下列位置找到 Visual Studio Package 範本：[Visual Basic]/[ **擴充性** ]、[C#]/[ **擴充性**] 或 [其他專案類型]/[ **擴充性**] 下的 [ **新增專案**] 對話方塊。  
  
## <a name="creating-a-command"></a>建立命令  
 所有命令、命令群組、功能表、工具列和工具視窗定義在 .vsct 檔案中。 如需詳細資訊，請參閱 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
 如果您使用封裝範本建立 VSPackage，請選取 [ **功能表命令** ] 來建立 .vsct 檔並定義預設的功能表命令。 如需詳細資訊，請參閱 <<c0> [ 建立具有功能表命令的擴充](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
#### <a name="to-add-a-command-to-the-ide"></a>將命令加入 IDE  
  
1. 開啟 .vsct 檔案。  
  
2. 在 `Symbols` 區段中，尋找包含群組和命令的 [GuidSymbol](../extensibility/guidsymbol-element.md) 項目。  
  
3. 為您要加入的每個功能表、群組或命令建立 [IDSymbol](../extensibility/idsymbol-element.md) 項目，如下列範例所示。  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name` 和 `GuidSymbol` 項目的 `IDSymbol` 屬性為每個新的功能表、群組或命令提供一組 GUID:ID。 `guid` 代表為 VSPackage 定義的命令集。 您可以定義多個命令集。 每組 GUID:ID 都必須是唯一的。  
  
4. 在 [ [按鈕](../extensibility/buttons-element.md) ] 區段中，建立 [按鈕](../extensibility/button-element.md) 項目來定義命令，如下列範例所示。  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1. 設定 `guid` 和 `id` 欄位，以符合新命令的 GUID:ID。  
  
   2. 設定 `priority` 屬性。  
  
        .vsct 使用 `priority` 屬性來決定按鈕與父群組中其他物件的相對位置。  
  
        具有較低優先順序值的命令會顯示在具有較高優先順序值的命令上方或左方。 允許重複的優先順序值，但具有相同優先順序之命令的相對位置會取決於 VSPackage 在執行階段的處理順序，而且該順序無法預先決定。  
  
        省略 `priority` 屬性會將其值設定為 0。  
  
   3. 設定 `type` 屬性。 在大部分情況下，其值為 `"Button"`。 如需其他有效按鈕類型的描述，請參閱 [Button Element](../extensibility/button-element.md)。  
  
5. 在按鈕定義中，建立包含 [ButtonText](../extensibility/strings-element.md) 項目的 [字串](../extensibility/buttontext-element.md) 項目，以包含顯示在 IDE 中的功能表名稱，並建立 [CommandName](../extensibility/commandname-element.md) 項目，以包含用於存取 [ **命令** ] 視窗之功能表的命令名稱。  
  
    如果按鈕文字字串包含 '&' 字元，使用者可以按 ALT 鍵及 '&' 後面緊接的字元來開啟功能表。  
  
    加入 `Tooltip` 項目會使得包含的文字在使用者將滑鼠指標停留在按鈕上時顯示。  
  
6. 加入 [圖示](../extensibility/icon-element.md) 項目來指定圖示，如果有的話，和命令一起顯示。 工具列上的按鈕需要圖示，但功能表項目不需要。 `guid` 項目的 `id` 和 `Icon` 必須符合 [區段中定義的](../extensibility/bitmap-element.md) 點陣圖 `Bitmaps` 項目。  
  
7. 視需要加入命令旗標，以變更按鈕的外觀和行為。 若要執行這個動作，請在功能表定義中加入 [CommandFlag](../extensibility/command-flag-element.md) 項目。  
  
8. 設定命令的父群組。 父群組可以是您建立的群組、來自另一個封裝的群組，或來自 IDE 的群組。 例如，若要將命令加入 Visual Studio 編輯工具列，放在 [ **註解** ] 和 [ **移除註解** ] 按鈕旁，請將父代設定為 guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT。 如果父代是使用者定義的群組，它必須是出現在 IDE 之功能表、工具列或工具視窗的子系。  
  
    您可以執行下列兩種方式之一，視您的設計而定：  
  
   - 在 `Button` 項目中，建立 [父代](../extensibility/parent-element.md) 項目，並將其 `guid` 和 `id` 欄位設定為裝載命令之群組的 Guid 和 ID，這個群組又稱為 *「主要父群組」* (primary parent group)。  
  
        下列範例會定義使用者定義功能表中所顯示的命令。  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   - 如果使用命令位置來放置命令，則可以省略 `Parent` 。 在 [區段之前建立](../extensibility/commandplacements-element.md) CommandPlacements `Symbols` 項目，然後加入具有命令 [和](../extensibility/commandplacement-element.md) 、 `guid` 和父代的 `id` CommandPlacement `priority`，如下列範例所示。  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
      建立多個有相同 GUID:ID 但有不同父代的命令位置，會使功能表出現在多個位置。 如需詳細資訊，請參閱 [CommandPlacements](../extensibility/commandplacements-element.md) 項目。  
  
    如需有關命令群組與父代的詳細資訊，請參閱[建立可重複使用群組的按鈕](../extensibility/creating-reusable-groups-of-buttons.md)。  
  
   此時，命令會顯示在 IDE 中，但沒有任何功能。 如果命令由封裝範本所建立，依預設它會有 顯示訊息的 Click 處理常式。  
  
## <a name="handling-the-new-command"></a>處理新的命令  
 Managed 程式碼的大部分命令可以由 Managed 封裝架構 (MPF) 來處理，方法是產生命令與 <xref:System.ComponentModel.Design.MenuCommand> 物件或 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 物件的關聯，並實作其事件處理常式。  
  
 對於直接使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面處理命令的程式碼，您必須實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面和其方法。 兩個最重要的方法是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>。  
  
1. 取得 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 執行個體，如下列範例所示。  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2. 建立 <xref:System.ComponentModel.Design.CommandID> 物件，其以要處理之命令的 GUID 和 ID 作為參數，如下列範例所示。  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Visual Studio 封裝範本提供兩個集合 `GuidList` 和 `PkgCmdIDList`，來保存命令的 GUID 和 ID。 這些會針對範本加入的命令自動填入，但對於您手動加入的命令，您也必須將 ID 項目加入 `PkgCmdIdList` 類別。  
  
     或者，您可以使用 GUID 的原始字串值和 ID 的整數值，填入 <xref:System.ComponentModel.Design.CommandID> 物件。  
  
3. 具現化 <xref:System.ComponentModel.Design.MenuCommand> 或 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 物件，指定處理命令的方法以及 <xref:System.ComponentModel.Design.CommandID>，如下列範例所示。  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     <xref:System.ComponentModel.Design.MenuCommand> 適用於靜態命令。 動態功能表項目顯示需要 QueryStatus 事件處理常式。 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 會加入 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件，此事件會在命令的主功能表開啟時發生，另外也會加入一些其他屬性，例如 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>。  
  
     封裝範本所建立的命令，依預設會在封裝類別的 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 方法中，傳遞到 `Initialize()` 物件。  
  
4. <xref:System.ComponentModel.Design.MenuCommand> 適用於靜態命令。 動態功能表項目顯示需要 QueryStatus 事件處理常式。 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 會加入 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件，此事件會在命令的主功能表開啟時發生，另外也會加入一些其他屬性，例如 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>。  
  
     封裝範本所建立的命令，依預設會在封裝類別的 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 方法中，傳遞到 `Initialize()` 物件。 Visual Studio 精靈使用 `Initialize` 來實作 `MenuCommand`方法。 針對動態功能表項目顯示，您必須將這變更為 `OleMenuCommand`，如下一個步驟所示。 此外，若要變更功能表項目文字，您必須將 TextChanges 命令旗標加入 .vsct 檔案中的功能表命令按鈕，如下列範例所示  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5. 將新的功能表命令傳遞給 <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> 介面的 <xref:System.ComponentModel.Design.IMenuCommandService> 方法。 依預設，會針對封裝範本所建立的命令而完成，如下列範例所示  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6. 實作處理命令的方法。  
  
#### <a name="to-implement-querystatus"></a>實作 QueryStatus  
  
1. QueryStatus 事件會在顯示命令之前發生。 這可讓該命令的屬性，在使用者看到之前便在事件處理常式中設定。 只有加入為 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 物件的命令可以存取此方法。  
  
    將 `EventHandler` 物件加入為處理命令而建立之 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 物件的 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 事件，如下列範例所示 (`menuItem` 是 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 執行個體)。  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler` 物件會得到在查詢功能表命令的狀態時所呼叫之方法的名稱。  
  
2. 實作命令的查詢狀態處理常式方法。 `object` `sender` 參數可以轉換成 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 物件，用來設定功能表命令的各種屬性，包括文字。 下表顯示 <xref:System.ComponentModel.Design.MenuCommand> 類別上的屬性 (MPF 類別 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 衍生自此類別)，這些屬性對應至 <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 旗標。  
  
   |MenuCommand 屬性|OLECMDF 旗標|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    若要變更功能表命令的文字，請使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> 物件上的 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 屬性，如下列範例所示。  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF 會自動處理不受支援或未知的群組案例。 除非已使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 方法將命令加入 <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> ，否則不支援命令。  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>使用 IOleCommandTarget 介面處理命令  
 對於直接使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面的程式碼，VSPackage 必須同時實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 介面的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 方法。 如果 VSPackage 實作專案階層架構，則應該改為實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 介面的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 方法。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法都是設計來接收單一命令集 `GUID` 和命令 ID 的陣列作為輸入。 我們建議 VSPackage 在單一呼叫中完全支援這個多 ID 的概念。 不過，只要未從其他 VSPackage 呼叫 VSPackage，您就可以假設命令陣列只包含一個命令 ID，因為 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 和 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法會按照妥善定義的順序執行。 如需有關路由的詳細資訊，請參閱 < [Vspackage 的命令路由](../extensibility/internals/command-routing-in-vspackages.md)。  
  
 對於直接使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面處理命令的程式碼，您必須在 VSPackage 中實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法來處理命令，如下所示。  
  
##### <a name="to-implement-the-querystatus-method"></a>實作 QueryStatus 方法  
  
1. 針對有效的命令傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 。  
  
2. 設定 `cmdf` 參數的 `prgCmds` 項目。  
  
    `cmdf` 項目的值是來自 <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 列舉值的邏輯聯集，藉由使用邏輯 OR (`|`) 運算子合併。  
  
    根據命令的狀態使用適當的列舉：  
  
   - 如果支援命令：  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - 如果此時應該看不見命令：  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - 如果命令切換為開，而且似乎已被點選：  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      在針對類型 `MenuControllerLatched`之功能表上主控的命令處理案例， `OLECMDF_LATCHED` 旗標標記的第一個命令即是啟動時功能表所顯示的預設命令。 如需 `MenuController` 功能表類型的詳細資訊，請參閱 [Menu Element](../extensibility/menu-element.md)。  
  
   - 如果目前已啟用命令：  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - 如果命令是快顯功能表的一部分，而且預設為隱藏：  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - 如果命令使用 `TEXTCHANGES` 旗標，請將 `rgwz` 參數的 `pCmdText` 項目設為命令的新文字，並將 `cwActual` 參數的 `pCmdText` 項目設為命令字串的大小。  
  
     對於錯誤狀況， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法必須處理下列錯誤情況：  
  
   - 如果 GUID 不明或不受支援，會傳回 `OLECMDERR_E_UNKNOWNGROUP`。  
  
   - 如果已知 GUID，但是命令 ID 不明或不受支援，會傳回 `OLECMDERR_E_NOTSUPPORTED`。  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法的 VSPackage 實作還必須傳回特定的錯誤碼，根據是否支援該命令和是否已成功處理命令而定。  
  
##### <a name="to-implement-the-exec-method"></a>實作 Exec 方法  
  
- 如果命令 `GUID` 不明，會傳回 `OLECMDERR_E_UNKNOWNGROUP`。  
  
- 如果 `GUID` 已知但命令 ID 不明時，會傳回 `OLECMDERR_E_NOTSUPPORTED`。  
  
- 如果 `GUID` 和命令 ID 符合 .vsct 檔中的命令所使用的 GUID:ID 配對，會執行與命令相關聯的程式碼並傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。  
  
## <a name="see-also"></a>另請參閱  
 [VSCT XML 結構描述參考](../extensibility/vsct-xml-schema-reference.md)   
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
