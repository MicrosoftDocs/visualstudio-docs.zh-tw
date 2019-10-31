---
title: 將功能表命令當地語系化 |Microsoft Docs
ms.date: 10/08/2019
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
ms.openlocfilehash: 94f71014440c55da0151d0ebd817aac9f5d2c7ed
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186272"
---
# <a name="localize-menu-commands"></a>將功能表命令當地語系化

您可以為您的 VSPackage 建立當地語系化的 *.vsct*檔案和當地語系化的 *.resx*檔案，然後更新專案檔以併入變更，以提供功能表和工具列命令的當地語系化文字。

如需如何將安裝體驗當地語系化的詳細資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)。

## <a name="localize-command-names"></a>將命令名稱當地語系化

在 Vspackage 中，功能表命令和工具列按鈕會定義在 *.vsct*檔案中。

1. 在**方案總管**中，將 *.vsct*檔案的名稱從 *.vsct*變更為*filename. en-us. .vsct*。

2. 為每個當地語系化語言製作 *.vsct*的複本。

    為每個複本*檔案名命名。 {Locale}. .vsct*，其中 *{Locale}* 是特定的文化特性名稱。 如需文化特性名稱值的清單，請參閱[Microsoft 指派的地區設定識別碼](/windows/uwp/publish/supported-languages)。

    這些*檔案名.Vsct*檔案將包含您封裝的當地語系化功能表文字。

3. 開啟每個*檔案名。* 要當地語系化文字的 .vsct 檔案。

   1. 針對特定語言，適當地修改[ButtonText](../extensibility/buttontext-element.md)元素的值。

   2. 如果您將提供當地語系化的圖示，請修改[點陣圖](../extensibility/bitmap-element.md)值以指向目標檔案。

      下列範例顯示用來開啟 [家族樹狀檢視器] 工具視窗之命令的英文和西班牙文按鈕文字。

      [*FamilyTree. en-us. .vsct*]

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

    [*FamilyTree.es-es. .vsct*]

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

## <a name="localize-other-text-resources"></a>將其他文字資源當地語系化

命令名稱以外的文字資源是在資源檔（ *.resx*）中定義。

1. 將*VSPackage*重新命名為*VSPackage*。

2. 為每個當地語系化的語言製作 VSPackage 的每個 *.resx*檔案的複本。

     為每個複製*VSPackage 命名。 {Locale} .resx*，其中 *{Locale}* 是特定的文化特性名稱。

3. 將*resources. .resx*重新命名為*resources*。

4. 為每個當地語系化的語言製作一份*Resources.-US .resx*檔案。

     為每個複製*資源命名。 {Locale} .resx*，其中 *{Locale}* 是特定的文化特性名稱。

5. 開啟每個 *.resx*檔案，以適當地修改特定語言和文化特性的字串值。 下列範例會顯示工具視窗標題列的當地語系化資源定義。

     [*Resources. en-us .resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-es .resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>將當地語系化的資源併入專案中

您必須修改*assemblyinfo.cs*檔案和專案檔，以併入當地語系化的資源。

1. 從**方案總管**的 [**屬性**] 節點中，在編輯器中開啟*assemblyinfo.cs*或*assemblyinfo* 。

2. 新增下列專案。

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     這會將美式英文設定為預設語言。

3. 卸載專案。

4. 在編輯器中開啟專案檔。

5. 在根 `Project` 元素中，加入 `PropertyGroup` 元素，其中包含符合您預設語言的 `UICulture` 元素。

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     這會將美式英文設定為 Windows Presentation Foundation （WPF）控制項的預設 UI 文化特性。

6. 找出包含 `EmbeddedResource` 元素的 `ItemGroup` 元素。

7. 在呼叫*VSPackage*的 `EmbeddedResource` 專案中，將 `ManifestResourceName` 元素取代為設定為 `VSPackage.en-US.Resources`的 `LogicalName` 元素，如下所示：

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. 針對每個當地語系化的語言，複製 `VsPackage.en-US`的 `EmbeddedResource` 專案，並將複本的**Include**屬性和**LogicalName**元素設定為目標地區設定。

9. 針對每個當地語系化的 `VSCTCompile` 專案，加入指向 `Menus.ctmenu`的 `ResourceName` 元素，如下列範例所示：

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. 儲存專案檔案並重載專案。

11. 建置專案。

     這會建立主要元件，以及每種語言的資源元件。 如需當地語系化部署程式的詳細資訊，請參閱[當地語系化 VSIX 封裝](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>請參閱

- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
