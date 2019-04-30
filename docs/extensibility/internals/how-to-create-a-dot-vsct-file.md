---
title: HOW TO：建立。Vsct 檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c671467f220e61de5ca9de56a2515a2e4836020
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418473"
---
# <a name="how-to-create-a-vsct-file"></a>HOW TO：建立.vsct 檔

有數種方式可建立以 XML 為基礎的 Visual Studio 命令資料表設定 (*.vsct*) 檔案。

- 您可以建立新的 VSPackage 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]封裝範本。

- 您可以使用以 XML 為基礎的命令資料表設定編譯器*Vsct.exe*，以產生從現有的檔案 *.ctc*檔案。

- 您可以使用*Vsct.exe*產生 *.vsct*從現有的檔案 *.cto*檔案。

- 您可以手動建立新 *.vsct*檔案。

  這篇文章說明如何以手動方式建立新 *.vsct*檔案。

### <a name="to-manually-create-a-new-vsct-file"></a>若要手動建立新的.vsct 檔

1. 啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

2. 在上**檔案**功能表上，指向**新增**，然後按一下**檔案**。

3. 在 **範本**窗格中，按一下**XML 檔案**，然後按一下 **開啟**。

4. 在上**檢視**功能表上，按一下**屬性**，顯示的 XML 檔案的內容。

5. 在 [**屬性**] 視窗中，按一下**瀏覽**按鈕**結構描述**屬性。

6. 在 XSD 結構描述的清單中，選取*vsct.xsd*結構描述。 如果它不在清單中，按一下**新增**，然後尋找 本機磁碟機上的檔案。 按一下 **確定**完畢時。

7. 在 XML 檔案中，輸入 *< CommandTable* ，然後按** 索引標籤**。輸入關閉標記*>*。

    此動作會建立基本 *.vsct*檔案。

8. 在 XML 檔案，您想要新增的項目填滿、 根據[VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。 如需詳細資訊，請參閱[撰寫.vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>HOW TO：從現有的.ctc 檔建立.vsct 檔

您可以建立以 XML 為基礎 *.vsct*現有命令資料表中的檔案 *.ctc*原始程式檔。 這樣做，您可以充分利用新的 XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令資料表 (VSCT) 編譯器格式。

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>從 .ctc 檔建立 .vsct 檔

1. 取得一份 Perl 語言。

2. 取得一份 Perl 指令碼*ConvertCTCToVSCT.pl*，通常位於 *\<Visual Studio SDK 安裝路徑 > \VisualStudioIntegration\Tools\bin*資料夾。

3. 取得一份 *.ctc*您想要轉換的來源檔案。

4. 將檔案放置在相同的目錄中。

5. 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令提示字元視窗中，瀏覽至目錄。

6. 類型

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    其中*PkgCmd.ctc*名稱 *.ctc*檔案並*PkgCmd.vsct*名稱 *.vsct*您想要建立的檔案。

    這個動作會建立新 *.vsct* XML 命令資料表原始程式檔。 您可以使用來編譯檔案*Vsct.exe*，使用 VSCT 編譯器，當您針對任何其他 *.vsct*檔案。

   > [!NOTE]
   > 您可以改善可讀性 *.vsct*藉由重新格式化 XML 註解的檔案。

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>HOW TO：從現有的.cto 檔建立.vsct 檔

您可以建立以 XML 為基礎 *.vsct*從現有的二進位檔的檔案 *.cto*檔案。 這樣做可讓您充分利用新的命令資料表編譯器格式。 此程序的運作，即使 *.cto*檔案已從編譯 *.ctc*檔案。 您可以編輯和編譯 *.vsct*到另一個.cto 檔的檔案。

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>從 .cto 檔建立 .vsct 檔

1. 取得的複本 *.cto*檔案和其對應 *.ctsym*檔案。

2. 將檔案放置在相同的目錄*vsct.exe*編譯器。

3. 在 Visual Studio 命令提示字元中，請移至 包含的目錄 *.cto*並 *.ctsym*檔案。

4. 類型

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     何處\<ctofilename\>名稱 *.cto*檔案中， \<vsctfilename\>名稱 *.vsct*檔案您想来建立，以及\<symfilename\>的名稱 *.ctsym*檔案。

     此程序建立新 *.vsct* XML 命令資料表編譯器檔案。 您可以編輯並編譯此檔案*vsct.exe*，使用 vsct 編譯器，當您針對任何其他 *.vsct*檔案。

## <a name="compile-the-code"></a>編譯程式碼
 只要加上 *.vsct*至專案的檔案並不會導致其進行編譯。 您必須將它納入建置流程中。

### <a name="to-add-a-vsct-file-to-project-compilation"></a>將專案編譯中加入.vsct 檔

1. 在編輯器中開啟您的專案檔。 如果載入專案時，您必須先卸載它。

2. 新增[ItemGroup 項目](../../msbuild/itemgroup-element-msbuild.md)包含`VSCTCompile`項目，如下列範例所示。

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName`元素應永遠設定為`Menus.ctmenu`。

3. 如果您的專案包含 *.resx*檔案中，新增`EmbeddedResource`包含的項目`MergeWithCTO`項目，如下列範例所示：

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     此標記應該進入`ItemGroup`包含內嵌的資源的項目。

4. 開啟封裝檔案，通常名為 *\<ProjectName\>Package.cs*或是 *\<ProjectName\>Package.vb*，在編輯器中。

5. 新增`ProvideMenuResource`屬性加入該套件類別，如下列範例所示。

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     第一個參數值必須符合的值`ResourceName`您在專案檔中定義的屬性。

## <a name="see-also"></a>另請參閱
- [撰寫.vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio 命令表檔案 (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)