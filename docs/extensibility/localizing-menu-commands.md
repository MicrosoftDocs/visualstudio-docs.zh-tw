---
title: 將功能表命令當地語系化 |Microsoft Docs
description: 瞭解如何為您的 VSPackage 建立當地語系化的 .vsct 檔案和當地語系化的 .resx 檔案，以提供功能表和工具列命令的當地語系化文字。
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 141fb0d8ba6746e7d299984461fb3ca739d931d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073257"
---
# <a name="localize-menu-commands"></a>當地語系化功能表命令

您可以為您的 VSPackage 建立當地語系化的 *.vsct* 檔案和當地語系化的 *.resx* 檔，然後更新專案檔以納入變更，以提供功能表和工具列命令的當地語系化文字。

如需如何將安裝體驗當地語系化的詳細資訊，請參閱將 [VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)。

## <a name="localize-command-names"></a>當地語系化命令名稱

在 Vspackage 中，會在 *.vsct* 檔案中定義功能表命令和工具列按鈕。

1. 在 **方案總管** 中，將 *.vsct* 檔案的名稱從 *.vsct* 變更為 *filename. .vsct*。

2. 為每個當地語系化語言建立檔案名的副本 *。 .vsct* 。

    命名每個複本 *的檔案名。 {Locale}. .vsct*，其中 *{Locale}* 是特定的文化特性名稱。 如需文化特性名稱值的清單，請參閱 [Microsoft 指派的地區設定識別碼](/windows/uwp/publish/supported-languages)。

    這些 *檔案名。.Vsct* 檔案將包含您套件的當地語系化功能表文字。

3. 開啟每個 *檔案名。.Vsct* 檔案以當地語系化文字。

   1. 適當地修改特定語言的 [ButtonText](../extensibility/buttontext-element.md) 元素值。

   2. 如果您將提供當地語系化的圖示，請修改 [點陣圖](../extensibility/bitmap-element.md) 值以指向目標檔案。

      下列範例會顯示命令的英文和西班牙文按鈕文字，以開啟 [家族樹狀檢視器] 工具視窗。

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

命令名稱以外的文字資源會定義在資源 (*.resx*) 檔案中。

1. 將 *VSPackage* 重新命名為 *VSPackage。*

2. 針對每個當地語系化的語言，製作一份 *VSPackage 的 .resx* 檔案。

     為每個複製 *VSPackage 命名。 {Locale} .resx*，其中 *{Locale}* 是特定的文化特性名稱。

3. 將 *resources* 重新命名為 *resources. en-us*。

4. 針對每個當地語系化的語言，製作一份 *資源的 en-us* 檔。

     命名每個複製 *資源。 {Locale} .resx*，其中 *{Locale}* 是特定的文化特性名稱。

5. 開啟每個 *.resx* 檔案，以適當地修改特定語言和文化特性的字串值。 下列範例會顯示工具視窗標題列的當地語系化資源定義。

     [*Resources： en-us*]

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

## <a name="incorporate-localized-resources-into-the-project"></a>將當地語系化的資源納入專案中

您必須修改 *assemblyinfo .cs* 檔案和專案檔，以併入當地語系化的資源。

1. 從 **方案總管** 中的 [**屬性**] 節點，在編輯器中開啟 *assemblyinfo .cs* 或 *assemblyinfo。*

2. 新增下列專案。

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     這會將 US 英文設定為預設語言。

3. 卸載專案。

4. 在編輯器中開啟專案檔。

5. 在根項目中，加入專案，其中 `Project` `PropertyGroup` 包含 `UICulture` 符合您的預設語言的元素。

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     這會將美式英文設定為 Windows Presentation Foundation (WPF) 控制項的預設 UI 文化特性。

6. 找出 `ItemGroup` 包含元素的元素 `EmbeddedResource` 。

7. 在呼叫 VSPackage 的專案中，將專案 `EmbeddedResource` 取代為 `ManifestResourceName` 設定為的元素，如下所示 `LogicalName` `VSPackage.en-US.Resources` ：

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. 針對每個當地語系化語言，複製的專案  `EmbeddedResource` `VsPackage.en-US` ，並將複本的 **Include** 屬性和 **LogicalName** 元素設定為目標地區設定。

9. 針對每個當地語系化 `VSCTCompile` 元素，加入 `ResourceName` 指向的專案 `Menus.ctmenu` ，如下列範例所示：

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. 儲存專案檔案，然後重載專案。

11. 建置專案。

     這會建立主要元件，以及每種語言的資源元件。 如需當地語系化部署程式的詳細資訊，請參閱將 [VSIX 封裝當地語系化](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>另請參閱

- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
