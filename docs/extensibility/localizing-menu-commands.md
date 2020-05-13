---
title: 當地語系化選單指令 |微軟文件
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702951"
---
# <a name="localize-menu-commands"></a>本地化選單指令

您可以透過為 VSPackage 建立本地化*的 .vsct*檔案和當地語系化的 *.resx*檔案,然後更新專案檔以合併更改,為選單和工具列命令提供當地語系化文本。

關於如何本地化安裝體驗的資訊,請參考[本地端 VSIX 套件](../extensibility/localizing-vsix-packages.md)。

## <a name="localize-command-names"></a>本地化指令名稱

在 VSPackages 中,功能表命令和工具列按鈕在 *.vsct*檔案中定義。

1. 在**解決方案資源管理員中**,將 *.vsct*檔案的名稱從*filename.vsct*更改為*filename.en-US.vsct*。

2. 為每個本地化語言創建*檔案名.en-US.vsct*的副本。

    命名每個複本*檔名。區域設置\.vsct*,其中 *[區域設置]* 是特定的區域性名稱。 有關區域性名稱值的清單,請參閱[Microsoft 分配的區域設置。](/windows/uwp/publish/supported-languages)

    這些檔*名。區域設定.vsct*檔將包含包的本地化選單文本。

3. 打開每個*檔名。區域設定.vsct*檔案以本地化文字。

   1. 根據需要修改針對特定語言的[ButtonText](../extensibility/buttontext-element.md)元素值。

   2. 如果要提供當地語系化圖示,請修改[Bitmap](../extensibility/bitmap-element.md)值以指向目標檔。

      下面的範例顯示打開「家譜資源管理器」工具視窗的命令的英語和西班牙文按鈕文本。

      [*Mid.en-US.vsct*]

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

## <a name="localize-other-text-resources"></a>本地化其他文字資源

命令名稱以外的文字資源在資源(*.resx*) 檔案中定義。

1. 重新命名*VSPackage.resx*到*VSPackage.en-US.resx*。

2. 為每個本地化語言複製*VSPackage.en-US.resx*檔。

     命名每個副本*VSPackage。區域設置\.resx*,其中 *[區域設置]* 是特定的區域性名稱。

3. 重新命名*資源.resx*到*資源.en-US.resx*。

4. 為每個本地化語言複製*參考資料.en-US.resx*檔案。

     命名每個副本*資源。區域設置\.resx*,其中 *[區域設置]* 是特定的區域性名稱。

5. 開啟每個 *.resx*檔以修改特定語言和區域性的字串值。 下面的範例顯示了工具視窗的標題列的本地化資源定義。

     【*資源.en-US.resx*]

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

## <a name="incorporate-localized-resources-into-the-project"></a>將本地化資源合併到項目中

您必須修改*assemblyinfo.cs*檔案和專案檔以合併當地語系化的資源。

1. 從**解決方案資源管理員**中的 **「屬性」** 節點中,在編輯器中打開*assemblyinfo.cs*或*assemblyinfo.vb。*

2. 添加以下項目。

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     這將美國英語設置為默認語言。

3. 卸載專案。

4. 在編輯器中打開專案檔。

5. 在根`Project`元素`PropertyGroup`中,添加具有與預設`UICulture`語言 匹配的元素的元素。

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     這將美國英語集為 Windows 演示文稿基礎 (WPF) 控件的預設 UI 區域性。

6. 找到包含`ItemGroup``EmbeddedResource`元素的元素。

7. 在`EmbeddedResource`呼叫*VSPackage.en-US.resx*的元素`ManifestResourceName`中,將`LogicalName`元素`VSPackage.en-US.Resources`取代為 設定為的元素,如下所示:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. 對於每個本地化`EmbeddedResource`語言,複製的`VsPackage.en-US`元素,並將副本的 **「包括」** 屬性和**邏輯名稱**元素設置為目標區域設置。

9. 到每個本地化`VSCTCompile`元素,新增`ResourceName``Menus.ctmenu`指向的元素,如以下範例所示:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. 保存專案檔並重新載入專案。

11. 建置專案。

     這將為每個語言創建主程式集和資源程式集。 有關本地化部署的資訊,請參閱[本地化 VSIX 套件](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>另請參閱

- [延伸選單與指令](../extensibility/extending-menus-and-commands.md)
- [全球化及當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
