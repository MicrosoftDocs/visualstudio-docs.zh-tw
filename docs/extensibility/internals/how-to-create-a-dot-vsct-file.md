---
title: HOW TO：建立.Vsct 檔案 |Microsoft Docs
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
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924177"
---
# <a name="how-to-create-a-vsct-file"></a>作法：建立 .vsct 檔案

有數種方式可建立以 XML 為基礎的 Visual Studio 命令資料表設定 ( *. .vsct*) 檔案。

- 您可以在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]套件範本中建立新的 VSPackage。

- 您可以使用以 XML 為基礎的命令資料表設定編譯器 ( *.vsct*), 從現有的 *.ctc*檔案產生檔案。

- 您可以使用 *.vsct* , 從現有的*cto*檔案產生 *.vsct*檔案。

- 您可以手動建立新的 *.vsct*檔案。

  本文說明如何以手動方式建立新的 *.vsct*檔案。

### <a name="to-manually-create-a-new-vsct-file"></a>手動建立新的 .vsct 檔案

1. 啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

2. 在上**檔案**功能表上，指向**新增**，然後按一下**檔案**。

3. 在 [**範本**] 窗格中, 按一下 [ **XML**檔案], 然後按一下 [**開啟**]。

4. 在 [ **View** ] 功能表上, 按一下 [**屬性**] 以顯示 XML 檔案的屬性。

5. 在 [**屬性**] 視窗中, 按一下 [**架構**] 屬性上的 [**流覽]** 按鈕。

6. 在 XSD 架構清單中, 選取 [ *.vsct* ] 架構。 如果不在清單中, 請按一下 [**新增**], 然後在本機磁片磁碟機上尋找檔案。 完成後, 請按一下 **[確定]** 。

7. 在 XML 檔案中, 輸入 *< CommandTable* , 然後按**tab**鍵。輸入 *>* 以關閉標記。

    此動作會建立基本的 *.vsct*檔案。

8. 根據[.VSCT xml 架構參考](../../extensibility/vsct-xml-schema-reference.md), 填入您想要加入之 XML 檔案的元素。 如需詳細資訊, 請參閱[.vsct files](../../extensibility/internals/authoring-dot-vsct-files.md)。

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>作法：從現有的 .ctc 檔案建立 .vsct 檔案

您可以從現有的命令資料表建立 XML *.vsct*檔。 *.ctc*原始程式檔。 這樣做，您可以充分利用新的 XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令資料表 (VSCT) 編譯器格式。

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>從 .ctc 檔建立 .vsct 檔

1. 取得一份 Perl 語言。

2. 取得 Perl 腳本*ConvertCTCToVSCT.pl*的複本, 通常位於 *\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\bin*資料夾中。

3. 取得您想要轉換之 *.ctc*原始程式檔的複本。

4. 將檔案放置在相同的目錄中。

5. 在 [ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令提示字元] 視窗中, 流覽至目錄。

6. 類型

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    其中*PkgCmd. .ctc*是 *.ctc*檔案的名稱, 而*PkgCmd. .vsct*是您想要建立之 *.vsct*檔案的名稱。

    此動作會建立新的 *.Vsct* XML 命令資料表來源檔案。 您可以使用 *.vsct*(.vsct 編譯器) 來編譯檔案, 就像任何其他 *.vsct*檔案一樣。

   > [!NOTE]
   > 您可以重新格式化 XML 批註, 以改善 *.vsct*檔案的可讀性。

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>作法：從現有的 cto 檔案建立 .vsct 檔案

您可以從現有的*cto*檔建立以 XML 為基礎的 *.vsct*檔案。 這樣做可讓您充分利用新的命令資料表編譯器格式。 即使*cto*檔案是從 *.ctc*檔案編譯, 此程式仍可運作。 您可以編輯 *.vsct*檔案, 並將其編譯成另一個 cto 檔案。

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>從 .cto 檔建立 .vsct 檔

1. 取得*cto*檔案的複本及其對應的 *.ctsym*檔案。

2. 將檔案放入與 *.vsct*相同的目錄中。

3. 在 Visual Studio 命令提示字元中, 移至包含*cto*和 *. .ctsym*檔案的目錄。

4. 類型

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     其中\<ctofilename\> \< \< \>是 cto 檔案的名稱、vsctfilename 是您想要建立的 .vsct 檔案名, 而 symfilename 是的名稱\> *.ctsym*檔案。

     此程式會建立新的 *.Vsct* XML 命令資料表編譯器檔案。 您可以使用 *.vsct*(.vsct 編譯器) 來編輯和編譯檔案, 就如同任何其他 *.vsct*檔案一樣。

## <a name="compile-the-code"></a>編譯程式碼
 只是將 *.vsct*檔案新增至專案並不會使其編譯。 您必須將它併入組建程式中。

### <a name="to-add-a-vsct-file-to-project-compilation"></a>若要將 .vsct 檔案加入至專案編譯

1. 在編輯器中開啟您的專案檔。 如果已載入專案, 您必須先將它卸載。

2. 加入包含`VSCTCompile`元素的[ItemGroup 元素](../../msbuild/itemgroup-element-msbuild.md), 如下列範例所示。

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     元素應一律設定為`Menus.ctmenu`。 `ResourceName`

3. 如果您的專案包含 *.resx*檔案, 請加入`EmbeddedResource`包含`MergeWithCTO`元素的元素, 如下列範例所示:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     此標記應該放在包含`ItemGroup`內嵌資源的元素內。

4. 在編輯器中, 開啟封裝檔案 (通常名為 *\<專案\>名稱 Package.cs*或 *\<專案名稱\>package .vb*)。

5. `ProvideMenuResource`將屬性新增至 package 類別, 如下列範例所示。

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     第一個參數值必須符合您在專案檔`ResourceName`中定義的屬性值。

## <a name="see-also"></a>另請參閱
- [撰寫 .vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio 命令資料表 (. .vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [.VSCT XML 架構參考](../../extensibility/vsct-xml-schema-reference.md)