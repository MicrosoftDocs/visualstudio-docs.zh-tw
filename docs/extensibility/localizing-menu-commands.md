---
title: "當地語系化 功能表命令 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 586f087e4c0cbd087bd06d7dc54a524b09ae21c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-menu-commands"></a>當地語系化 功能表命令
您可以提供當地語系化的文字的功能表和工具列命令藉由建立當地語系化的.vsct 檔案，並為您的 VSPackage，然後更新專案檔的變更當地語系化的.resx 檔。  
  
 如需如何當地語系化安裝體驗的詳細資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="localizing-command-names"></a>當地語系化的命令名稱  
 在 Vspackage 中，功能表命令和工具列按鈕會定義在.vsct 檔案中。  
  
1.  在**方案總管 中**，變更從.vsct 檔的名稱*filename*.vsct 來*filename*.en US.vsct。  
  
2.  建立一份*filename*.en-US.vsct 每個當地語系化語言。  
  
     命名每個複本*filename*。*地區設定*.vsct，其中*地區設定*是特定文化特性名稱。 如需文化特性名稱值的清單，請參閱[microsoft 指派的地區設定識別碼](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx)。  
  
     這些*filename*。*地區設定*.vsct 檔會包含當地語系化的功能表文字，為您的封裝。  
  
3.  開啟每一個*filename*。*地區設定*.vsct 檔的文字當地語系化。  
  
    1.  修改[ButtonText](../extensibility/buttontext-element.md)為適合特定語言值的元素。  
  
    2.  如果您將會提供當地語系化的圖示，修改[點陣圖](../extensibility/bitmap-element.md)值指向的目標檔案。  
  
     下列範例會顯示英文和西班牙文按鈕文字，以開啟 家庭樹狀結構總管工具視窗命令。  
  
     [FamilyTree.en US.vsct]  
  
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
  
     [FamilyTree.es ES.vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>當地語系化文字中的其他資源  
 命令名稱以外的文字資源的資源 (.resx) 檔中定義。  
  
1.  重新命名 VSPackage.en US.resx VSPackage.resx。  
  
2.  請針對每個當地語系化的語言 VSPackage.en US.resx 檔案的副本。  
  
     每個複本 VSPackage 的名稱。*地區設定*.resx，其中*地區設定*是特定文化特性名稱。  
  
3.  重新命名 Resources.en US.resx Resources.resx。  
  
4.  請針對每個當地語系化的語言 Resources.en US.resx 檔案的副本。  
  
     命名每個複本的資源。*地區設定*.resx，其中*地區設定*是特定文化特性名稱。  
  
5.  開啟每個.resx 檔案修改適合特定語言和文化特性的字串值。 下列範例會顯示當地語系化的資源定義工具視窗的標題列。  
  
     [Resources.en US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>併入專案中當地語系化的資源  
 您必須修改 assemblyinfo.cs 檔案和專案檔案即可將當地語系化的資源。  
  
1.  從**屬性**節點**方案總管 中**，在編輯器中開啟 assemblyinfo.cs 或 assemblyinfo.vb。  
  
2.  新增下列項目。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     英文 （美國） 設定為預設語言。  
  
3.  卸載專案。  
  
4.  在編輯器中開啟專案檔。  
  
5.  找出`ItemGroup`包含項目`EmbeddedResource`項目。  
  
6.  在`EmbeddedResource`VSPackage.en US.resx，會呼叫的項目取代`ManifestResourceName`具有項目`LogicalName`項目，設定為`VSPackage.en-US.Resources`、，如下所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  針對每個當地語系化的語言複製`EmbeddedResource`VsPackage.en 美式和集合的項目**Include**屬性和**LogicalName**複製到目標地區設定，如下列所示的項目範例。  
  
8.  每個當地語系化`VSCTCompile`項目，加入`ResourceName`指向項目的`Menus.ctmenu`，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. 儲存專案檔，並重新載入專案。  
  
10. 建置專案。  
  
     這樣會建立主要組件，以及每種語言的資源組件。 當地語系化的部署程序的資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [MenuCommand 對比OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)