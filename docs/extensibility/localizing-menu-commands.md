---
title: 將功能表命令當地語系化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62c6011d1a04b60d1bd0cc538e9560d8977f9799
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344663"
---
# <a name="localize-menu-commands"></a>將功能表命令當地語系化
您也可以建立當地語系化的功能表和工具列命令提供當地語系化的文字 *.vsct*檔案，與當地語系化 *.resx*的 VSPackage，然後更新專案檔以納入的檔案變更。

 如需如何當地語系化安裝體驗的詳細資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。

## <a name="localize-command-names"></a>命令名稱當地語系化
 在 Vspackage 中，功能表命令和工具列按鈕中定義 *.vsct*檔案。

1. 在 [**方案總管] 中**，變更的名稱 *.vsct*檔案從*filename.vsct*至*filename.en US.vsct*。

2. 建立一份*filename.en US.vsct*每個當地語系化語言。

    命名每個複本*檔案名稱。 {地區設定}.vsct*，其中 *{地區設定}* 是特定文化特性名稱。 如需文化特性名稱值的清單，請參閱 < [Microsoft 指派的地區設定識別碼](/windows/uwp/publish/supported-languages)。

    這些*檔案名稱。Locale.vsct*檔會包含當地語系化的功能表文字，為您的封裝。

3. 開啟每一個*檔案名稱。Locale.vsct*當地語系化文字的檔案。

   1. 修改[ButtonText](../extensibility/buttontext-element.md)值為適用於特定語言的元素。

   2. 如果您將會提供當地語系化的圖示，修改[點陣圖](../extensibility/bitmap-element.md)值以指向目標檔案。

      下列範例會顯示英文和西班牙文按鈕文字，以開啟家譜 Explorer 工具視窗命令。

      [*FamilyTree.en-US.vsct*]

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

    [*FamilyTree.es-ES.vsct*]

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

## <a name="localize-other-text-resources"></a>當地語系化的文字中的其他資源
 文字命令名稱以外的資源定義中資源 ( *.resx*) 檔案。

1. 重新命名*VSPackage.resx*要*VSPackage.en US.resx*。

2. 建立一份*VSPackage.en US.resx*檔案，每個當地語系化語言。

     命名每個複本*VSPackage。 {地區設定}.resx*，其中 *{地區設定}* 是特定文化特性名稱。

3. 重新命名*Resources.resx*要*Resources.en-us.resx*。

4. 建立一份*Resources.en-us.resx*檔案，每個當地語系化語言。

     命名每個複本*資源。 {地區設定}.resx*，其中 *{地區設定}* 是特定文化特性名稱。

5. 開啟每一個 *.resx*檔案修改的字串值為適合特定語言和文化特性。 下列範例會顯示工具視窗的標題列的當地語系化的資源定義。

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>

    ```

## <a name="incorporate-localized-resources-into-the-project"></a>併入專案中當地語系化的資源
 您必須修改*assemblyinfo.cs*檔案和專案檔案，來將當地語系化的資源。

1. 從**屬性**中的節點**方案總管**，開啟*assemblyinfo.cs*或是*assemblyinfo.vb*在編輯器中。

2. 新增下列項目。

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     英文 （美國） 設定為預設語言。

3. 卸載專案。

4. 在編輯器中開啟專案檔。

5. 找出`ItemGroup`包含的項目`EmbeddedResource`項目。

6. 在`EmbeddedResource`呼叫的項目*VSPackage.en US.resx*，取代`ManifestResourceName`項目`LogicalName`項目，設定為`VSPackage.en-US.Resources`、，如下所示。

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

7. 針對每個當地語系化的語言，複製`EmbeddedResource`項目`VsPackage.en-US`，並將**Include**屬性和**LogicalName**的複製到目標地區設定，如下列所示的項目範例。

8. 每個當地語系化`VSCTCompile`項目，新增`ResourceName`指向的項目`Menus.ctmenu`，如下列範例所示。

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
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [Menucommand 對比OleMenuCommand](../extensibility/menucommands-vs-olemenucommands.md)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)