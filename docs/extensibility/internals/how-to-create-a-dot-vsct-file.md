---
title: 如何：創建一個 。Vsct 檔 |微軟文檔
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3155ff69db461e652b11ff6e8ec6d405000244f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303166"
---
# <a name="how-to-create-a-vsct-file"></a>如何：創建 .vsct 檔

有幾種方法可以創建基於 XML 的 Visual Studio 命令表配置 *（.vsct*） 檔。

- 您可以在包範本中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]創建新的 VS 包。

- 您可以使用基於 XML 的命令表配置編譯器*Vsct.exe*從現有的 *.ctc*檔生成檔。

- 您可以使用*Vsct.exe*從現有的 *.cto*檔生成 *.vsct*檔。

- 您可以手動創建新的 *.vsct*檔。

  本文介紹如何手動創建新的 *.vsct*檔。

### <a name="to-manually-create-a-new-vsct-file"></a>手動創建新的 .vsct 檔

1. 啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

2. 在 [ **檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **檔案**]。

3. 在 **"範本"** 窗格中，按一下**XML 檔**，然後按一下"**打開**"。

4. 在 **"視圖"** 功能表上，按一下 **"屬性**"以顯示 XML 檔的屬性。

5. 在 **"屬性"** 視窗中，按一下 **"架構**"屬性上的 **"流覽**"按鈕。

6. 在 XSD 架構清單中，選擇*vsct.xsd*架構。 如果不在清單中，請按一下"**添加**"，然後在本地磁碟機上查找該檔。 完成後按一下 **"確定**"。

7. 在 XML 檔中，鍵入*命令表<，* 然後按**Tab**。通過鍵入*>* 關閉標記。

    此操作將創建一個基本*的 .vsct*檔。

8. 根據[VSCT XML 架構引用](../../extensibility/vsct-xml-schema-reference.md)，填寫要添加的 XML 檔的元素。 有關詳細資訊，請參閱作者[.vsct 檔](../../extensibility/internals/authoring-dot-vsct-files.md)。

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>如何：從現有的 .ctc 檔創建 .vsct 檔

可以從現有命令表 *.ctc*原始檔案創建基於 XML 的 *.vsct*檔。 這樣做，您可以充分利用新的 XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令資料表 (VSCT) 編譯器格式。

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>從 .ctc 檔建立 .vsct 檔

1. 取得一份 Perl 語言。

2. 獲取 Perl 腳本*ConvertCTCToVSCT.pl*的副本，通常位於*\<Visual Studio SDK 安裝路徑>_VisualStudio集成\工具\bin*資料夾中。

3. 獲取要轉換的 *.ctc*原始檔案的副本。

4. 將檔案放置在相同的目錄中。

5. 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令提示視窗中，導航到目錄。

6. 類型

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    *其中 PkgCmd.ctc*是 *.ctc*檔的名稱 *，PkgCmd.vsct*是要創建的 *.vsct*檔的名稱。

    此操作將創建新的 *.vsct* XML 命令表原始檔案。 您可以使用 VSCT 編譯器*Vsct 編譯器 Vsct exe*編譯檔，就像使用任何其他 *.vsct*檔一樣。

   > [!NOTE]
   > 您可以通過重新格式化 XML 注釋來提高 *.vsct*檔的可讀性。

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>如何：從現有的 .cto 檔創建 .vsct 檔

可以從現有的二進位 *.cto*檔創建基於 XML 的 *.vsct*檔。 這樣做可讓您充分利用新的命令資料表編譯器格式。 即使 *.cto*檔是從 *.ctc*檔編譯的，此過程也有效。 您可以將 *.vsct*檔編輯和編譯為另一個 .cto 檔。

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>從 .cto 檔建立 .vsct 檔

1. 獲取 *.cto*檔及其相應的 *.ctsym*檔的副本。

2. 將檔放入與*vsct.exe*編譯器相同的目錄中。

3. 在 Visual Studio 命令提示符下，轉到包含 *.cto*和 *.ctsym*檔的目錄。

4. 類型

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     其中\<ctofilename\>是 *.cto*檔的名稱\<，fctfilename\>是要創建的 *.vsct*檔的名稱\<，而 symfilename\>是 *.ctsym*檔的名稱。

     此過程創建一個新的 *.vsct* XML 命令表編譯器檔。 您可以使用*vsct.exe（vsct*編譯器）編輯和編譯該檔，就像任何其他 *.vsct*檔一樣。

## <a name="compile-the-code"></a>編譯程式碼
 簡單地將 *.vsct*檔添加到專案中不會導致它編譯。 您必須將其合併到生成過程中。

### <a name="to-add-a-vsct-file-to-project-compilation"></a>將 .vsct 檔添加到專案編譯

1. 在編輯器中打開專案檔案。 如果載入了專案，則必須首先卸載它。

2. 添加包含`VSCTCompile`元素的[ItemGroup 元素](../../msbuild/itemgroup-element-msbuild.md)，如以下示例所示。

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     元素`ResourceName`應始終設置為`Menus.ctmenu`。

3. 如果專案包含 *.resx*檔，請添加包含`EmbeddedResource``MergeWithCTO`元素的元素，如以下示例所示：

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     此標記應進入包含嵌入資源`ItemGroup`的元素內。

4. 在編輯器中打開包檔，通常命名為*\<\>ProjectName Package.cs*或*\<ProjectName\>包.vb。*

5. 向`ProvideMenuResource`包類添加屬性，如以下示例所示。

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     第一個參數值必須與在專案檔案中`ResourceName`定義的屬性的值匹配。

## <a name="see-also"></a>另請參閱
- [作者 .vsct 檔](../../extensibility/internals/authoring-dot-vsct-files.md)
- [視覺化工作室命令表 （.vsct） 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 架構引用](../../extensibility/vsct-xml-schema-reference.md)