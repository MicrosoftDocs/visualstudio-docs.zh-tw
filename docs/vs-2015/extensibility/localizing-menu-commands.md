---
title: 將功能表命令當地語系化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686127"
---
# <a name="localizing-menu-commands"></a>將功能表命令當地語系化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以為您的 VSPackage 建立當地語系化的 .vsct 檔案和當地語系化的 .resx 檔，然後更新專案檔以納入變更，以提供功能表和工具列命令的當地語系化文字。  
  
 如需如何將安裝體驗當地語系化的詳細資訊，請參閱 [當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="localizing-command-names"></a>當地語系化命令名稱  
 在 Vspackage 中，會在 .vsct 檔案中定義功能表命令和工具列按鈕。  
  
1. 在 **方案總管**中，將 .vsct 檔案的 *名稱從 .vsct*變更為 *filename*. .vsct。  
  
2. 為每個當地語系化語言建立 *檔案名*的副本。 .vsct。  
  
    命名每個複本的*檔案名*。.Vsct，其中*locale*是特定的文化特性*名稱。* 如需文化特性名稱值的清單，請參閱 [Microsoft 指派的地區設定識別碼](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx)。  
  
    這些*檔案名*。.Vsct 檔案將包含您套件的當地語系化功能表*文字。*  
  
3. 開啟每個 *檔案名*。* *.Vsct 檔案以當地語系化文字。  
  
   1. 適當地修改特定語言的 [ButtonText](../extensibility/buttontext-element.md) 元素值。  
  
   2. 如果您將提供當地語系化的圖示，請修改 [點陣圖](../extensibility/bitmap-element.md) 值以指向目標檔案。  
  
      下列範例會顯示命令的英文和西班牙文按鈕文字，以開啟 [家族樹狀檢視器] 工具視窗。  
  
      [FamilyTree. en-us. .vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Family Tree Explorer</ButtonText>  
     </Strings>  
   </Button>  
   ```  
  
    [FamilyTree.es-ES. .vsct]  
  
   ```xml  
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <Icon guid="guidImages" id="bmpPic2" />  
     <Strings>  
       <CommandName>cmdidFamilyTree</CommandName>  
       <ButtonText>Explorar el arbol genealogico</ButtonText>  
     </Strings>  
   </Button>  
  
   ```  
  
## <a name="localizing-other-text-resources"></a>當地語系化其他文字資源  
 命令名稱以外的文字資源會定義在資源 ( .resx) 檔案中。  
  
1. 將 VSPackage 重新命名為 VSPackage。  
  
2. 針對每個當地語系化的語言，製作一份 VSPackage 的 .resx 檔案。  
  
     為每個複製 VSPackage 命名。*Locale*，其中 *locale* 是特定的文化特性名稱。  
  
3. 將 Resources 重新命名為 Resources. en-us。  
  
4. 針對每個當地語系化的語言，製作一份資源的 en-us 檔。  
  
     命名每個複製資源。*Locale*，其中 *locale* 是特定的文化特性名稱。  
  
5. 開啟每個 .resx 檔案，以適當地修改特定語言和文化特性的字串值。 下列範例會顯示工具視窗標題列的當地語系化資源定義。  
  
     [Resources： en-us]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES .resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>將當地語系化的資源併入專案中  
 您必須修改 assemblyinfo.cs 檔案和專案檔，以併入當地語系化的資源。  
  
1. 從**方案總管**中的 [**屬性**] 節點，在編輯器中開啟 assemblyinfo.cs 或 assemblyinfo。  
  
2. 新增下列專案。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     這會將 US 英文設定為預設語言。  
  
3. 卸載專案。  
  
4. 在編輯器中開啟專案檔。  
  
5. 找出 `ItemGroup` 包含元素的元素 `EmbeddedResource` 。  
  
6. 在 `EmbeddedResource` 呼叫 VSPackage 的元素中，將專案取代為 `ManifestResourceName` `LogicalName` 元素，並將設定為 `VSPackage.en-US.Resources` ，如下所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. 針對每個當地語系化的語言，複製  `EmbeddedResource` VsPackage 的元素，並將複本的 **Include** 屬性和 **LogicalName** 元素設定為目標地區設定，如下列範例所示。  
  
8. 針對每個當地語系化 `VSCTCompile` 元素，加入 `ResourceName` 指向的專案 `Menus.ctmenu` ，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. 儲存專案檔案，然後重載專案。  
  
10. 建置專案。  
  
     這會建立主要元件，以及每種語言的資源元件。 如需當地語系化部署流程的詳細資訊，請參閱[當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [Menucommand 對比與 OleMenuCommands 的比較](../misc/menucommands-vs-olemenucommands.md)   
 [全球化和當地語系化](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
