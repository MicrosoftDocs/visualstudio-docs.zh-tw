---
title: 將功能表命令當地語系化 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ce3cbbf101e357f761ffaf256d0b130a0c005fdb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488891"
---
# <a name="localizing-menu-commands"></a>將功能表命令當地語系化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[當地語系化功能表命令](https://docs.microsoft.com/visualstudio/extensibility/localizing-menu-commands)。  
  
您可以提供當地語系化的文字之功能表和工具列命令藉由建立當地語系化的.vsct 檔案和當地語系化的.resx 檔案的 VSPackage，然後更新專案檔才能將變更。  
  
 如需如何當地語系化安裝體驗的詳細資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="localizing-command-names"></a>當地語系化的命令名稱  
 在 Vspackage 中，功能表命令和工具列按鈕會定義在.vsct 檔案中。  
  
1.  中**方案總管 中**，變更從.vsct 檔的名稱*filename*.vsct 來*filename*.en US.vsct。  
  
2.  建立一份*filename*.en-US.vsct 每個當地語系化語言。  
  
     命名每個複本*檔名*。*地區設定*.vsct，其中*地區設定*是特定文化特性名稱。 如需文化特性名稱值的清單，請參閱 <<c0> [ 由 Microsoft 指派的地區設定識別碼](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx)。  
  
     這些*檔名*。*地區設定*.vsct 檔會包含當地語系化的功能表文字，為您的封裝。  
  
3.  開啟每一個*檔名*。*地區設定*.vsct 檔當地語系化文字。  
  
    1.  修改[ButtonText](../extensibility/buttontext-element.md)值為適用於特定語言的元素。  
  
    2.  如果您將會提供當地語系化的圖示，修改[點陣圖](../extensibility/bitmap-element.md)值以指向目標檔案。  
  
     下列範例會顯示英文和西班牙文按鈕文字，以開啟家譜 Explorer 工具視窗命令。  
  
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
  
## <a name="localizing-other-text-resources"></a>當地語系化的文字中的其他資源  
 資源 (.resx) 檔案中定義的文字命令名稱以外的資源。  
  
1.  重新命名 VSPackage.en US.resx VSPackage.resx。  
  
2.  請針對每個當地語系化的語言 VSPackage.en US.resx 檔案的複本。  
  
     命名每個複本的 VSPackage。*地區設定*.resx，其中*地區設定*是特定文化特性名稱。  
  
3.  重新命名 Resources.en-us.resx Resources.resx。  
  
4.  請針對每個當地語系化的語言 Resources.en-us.resx 檔案的複本。  
  
     命名每個複本的資源。*地區設定*.resx，其中*地區設定*是特定文化特性名稱。  
  
5.  開啟每個.resx 檔案，以修改適用於特定的語言和文化特性的字串值。 下列範例會顯示工具視窗的標題列的當地語系化的資源定義。  
  
     [Resources.en-us.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>併入專案中當地語系化的資源  
 您必須修改 assemblyinfo.cs 檔案和要納入的當地語系化的資源的專案檔。  
  
1.  從**屬性**中的節點**方案總管 中**，在編輯器中開啟 assemblyinfo.cs 或 assemblyinfo.vb。  
  
2.  新增下列項目。  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     英文 （美國） 設定為預設語言。  
  
3.  卸載專案。  
  
4.  在編輯器中開啟專案檔。  
  
5.  找出`ItemGroup`包含的項目`EmbeddedResource`項目。  
  
6.  在`EmbeddedResource`項目，會呼叫 VSPackage.en US.resx，取代`ManifestResourceName`項目`LogicalName`項目，設定為`VSPackage.en-US.Resources`、，如下所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  針對每個當地語系化的語言，複製`EmbeddedResource`VsPackage.en 美國，並將設定項目**Include**屬性並**LogicalName**的複製到目標地區設定，如下列所示的項目範例。  
  
8.  每個當地語系化`VSCTCompile`項目，新增`ResourceName`指向的項目`Menus.ctmenu`，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. 儲存專案檔，並重新載入專案。  
  
10. 建置專案。  
  
     這會建立主要組件，並針對每種語言的資源組件。 如需部署程序的當地語系化資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>另請參閱  
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [MenuCommand 對比OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [全球化和當地語系化](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)

